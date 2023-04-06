# 🔐 Isolated Storage

<figure><img src="../../.gitbook/assets/isolated storage.webp" alt=""><figcaption></figcaption></figure>

#### Portal is designed to host multiple parties without them affecting each other's storage space under any condition.

## DataStoreUtils Library

DataStore is a storage management tool designed to create a safe and scalable storage layout with the help of <mark style="color:purple;">**IDs**</mark> and <mark style="color:purple;">**KEYs**</mark>.&#x20;

Creating a sustainable development environment, even in ever changing technology.

#### With DataStore, Portal achieves 3 goals:

* A Dynamic Struct that is defined with the "TYPE" parameter, that can hold any amount of parameters, instead of only 16 _(max # of variables a struct can hold in Solidity)._
* Make it very easy to build new classes that have different parameters and functionalities, without altering the codebase.
* Separating the storage space of the contract, allowing Portal to maintain multiple parties without any friction.
* Ensuring the variable types: uint, address, and bytes.

## <mark style="color:purple;">Deep Dive</mark>

Storage Management library for dynamic structs based on data types.

#### The DataStore Struct

{% code title="DataStoreLib.sol" %}
```solidity
  struct DataStore {
    // type[0,1,2,3...] => ID list
    mapping(uint256 => uint256[]) allIdsByType;
    // keccak(id, key) => data
    mapping(bytes32 => uint256) UintData;
    mapping(bytes32 => bytes) BytesData;
    mapping(bytes32 => address) AddressData;
  }
```
{% endcode %}

Within the struct, there are 4 different mappings to serve different types of storage.

#### Generating an ID and Key

{% code title="" %}
```solidity
  function generateId(
    bytes memory NAME,
    uint256 TYPE
  ) internal pure returns (uint256 id) {
    id = uint256(keccak256(abi.encodePacked(NAME, TYPE)));
  }
  
  function getKey(
    uint256 _id,
    bytes32 _param
  ) internal pure returns (bytes32 key) {
    key = keccak256(abi.encodePacked(_id, _param));
  }
```
{% endcode %}

* IDs should be unique.
* Keys are bound to IDs, ensuring 2 IDs with same parameters can not share a storage slot.
* TYPEs are explicit, 4 representing Operators, 5 representing pools, and so on...
* NAMEs should be guarded within the same TYPE, meaning there can only be 1 entity with a given NAME and TYPE.

#### Sample Write Operation

{% code title="DataStoreLib.sol" %}
```solidity
   function writeUintForId(
    DataStore storage self,
    uint256 _id,
    bytes32 _key,
    uint256 data
  ) public {
    self.UintData[keccak256(abi.encodePacked(_id, _key))] = data;
  }
  
```
{% endcode %}

Basically, it takes the id and key pair encoded, secures a slot in the mapping for the id & key pair, and assigns the data to slot in the UintData mapping where the DataStore struct is taken as a storage argument. Every write operation in the library follows the same procedure.

#### Sample Read Operation

{% code title="DataStoreLib.sol" %}
```solidity
 function readBytesForId(
    DataStore storage self,
    uint256 _id,
    bytes32 _key
  ) public view returns (uint256 data) {
    data = self.BytesData[keccak256(abi.encodePacked(_id, _key))];
  }
```
{% endcode %}

This is also a typical read operation in the library, getting the data from the assigned slot with the given id and key pair, and returning the data publicly with the view restriction.

## <mark style="color:purple;">Reading the DataStore Through Portal</mark>&#x20;

Portal has a public endpoint for the view functions of the DataStore.&#x20;

This provides access to all data stored in the Portal, without needing to go through the docs, and scan through all the functions 🙂

<pre class="language-solidity" data-title="Portal.sol"><code class="lang-solidity"><strong>function generateId(
</strong>    string calldata _name,
    uint256 _type
  ) external pure virtual override returns (uint256 id) {
    id = uint256(keccak256(abi.encodePacked(_name, _type)));
  }
</code></pre>

* _generateId()_ Mimics the DataStore.generateId for string inputs.

{% code title="Portal.sol" %}
```solidity
  function getKey(
    uint256 id,
    bytes32 param
  ) external pure virtual override returns (bytes32 key) {
    return DataStoreUtils.getKey(_id, _param);
  }
```
{% endcode %}

* An example key generation can be:

```javascript
Portal.getKey(Portal.generateId("poolName", 5), getBytes32("surplus"));
Portal.getKey(Portal.generateId("operatorName", 5), getBytes32("totalValidators"));
```

#### Reading Simple Data

* An example read operation:

```javascript
Portal.readUintForId(Portal.generateId("poolName", 5), getBytes32("surplus"));
```

\---

{% code title="Portal.sol" %}
```solidity
  function readUintForId(
    uint256 id,
    bytes32 key
  ) external view virtual override returns (uint256 data) {
    data = DATASTORE.readUintForId(id, key);
  }

  function readAddressForId(
    uint256 id,
    bytes32 key
  ) external view virtual override returns (address data) {
    data = DATASTORE.readAddressForId(id, key);
  }

  function readBytesForId(
    uint256 id,
    bytes32 key
  ) external view virtual override returns (bytes memory data) {
    data = DATASTORE.readBytesForId(id, key);
  }
```
{% endcode %}

#### Reading an array&#x20;

* Currently only arrays are: `validators` and `interfaces`
* &#x20;Getting length of an array:

```javascript
Portal.readUintForId(Portal.generateId("poolName", 5), getBytes32("validators"));
```

* An example read operation on arrays:

```javascript
Portal.readUintForId(Portal.generateId("poolName", 5), getBytes32("validators"), 3);
```

\---

{% code title="Portal.sol" %}
```solidity
function readUintArrayForId(
    uint256 id,
    bytes32 key,
    uint256 index
  ) external view virtual override returns (uint256 data) {
    data = DATASTORE.readUintArrayForId(id, key, index);
  }

  function readBytesArrayForId(
    uint256 id,
    bytes32 key,
    uint256 index
  ) external view virtual override returns (bytes memory data) {
    data = DATASTORE.readBytesArrayForId(id, key, index);
  }

  function readAddressArrayForId(
    uint256 id,
    bytes32 key,
    uint256 index
  ) external view virtual override returns (address data) {
    data = DATASTORE.readAddressArrayForId(id, key, index);
  
```
{% endcode %}

