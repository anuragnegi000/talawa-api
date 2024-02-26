[talawa-api](../README.md) / [Exports](../modules.md) / utilities/graphQLConnection/transformToDefaultGraphQLConnection

# Module: utilities/graphQLConnection/transformToDefaultGraphQLConnection

## Table of contents

### Type Aliases

- [CreateCursor](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#createcursor)
- [CreateNode](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#createnode)
- [TransformToDefaultGraphQLConnectionArguments](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#transformtodefaultgraphqlconnectionarguments)

### Functions

- [transformToDefaultGraphQLConnection](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#transformtodefaultgraphqlconnection)

## Type Aliases

### CreateCursor

Ƭ **CreateCursor**\<`T0`\>: (`object`: `T0`) =\> `string`

This is typescript type of the callback function `createCursor`.

#### Type parameters

| Name |
| :------ |
| `T0` |

#### Type declaration

▸ (`object`): `string`

##### Parameters

| Name | Type |
| :------ | :------ |
| `object` | `T0` |

##### Returns

`string`

#### Defined in

[src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts:11](https://github.com/PalisadoesFoundation/talawa-api/blob/62d6dc4/src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts#L11)

___

### CreateNode

Ƭ **CreateNode**\<`T0`, `T1`\>: (`object`: `T0`) =\> `T1`

This is typescript type of the callback function `createNode`.

#### Type parameters

| Name |
| :------ |
| `T0` |
| `T1` |

#### Type declaration

▸ (`object`): `T1`

##### Parameters

| Name | Type |
| :------ | :------ |
| `object` | `T0` |

##### Returns

`T1`

#### Defined in

[src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts:16](https://github.com/PalisadoesFoundation/talawa-api/blob/62d6dc4/src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts#L16)

___

### TransformToDefaultGraphQLConnectionArguments

Ƭ **TransformToDefaultGraphQLConnectionArguments**\<`T0`, `T1`, `T2`\>: `Object`

#### Type parameters

| Name |
| :------ |
| `T0` |
| `T1` |
| `T2` |

#### Type declaration

| Name | Type |
| :------ | :------ |
| `createCursor?` | [`CreateCursor`](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#createcursor)\<`T1`\> |
| `createNode?` | [`CreateNode`](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#createnode)\<`T1`, `T2`\> |
| `objectList` | `T1`[] |
| `parsedArgs` | [`ParsedGraphQLConnectionArguments`](utilities_graphQLConnection_parseGraphQLConnectionArguments.md#parsedgraphqlconnectionarguments)\<`T0`\> |
| `totalCount` | `number` |

#### Defined in

[src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts:18](https://github.com/PalisadoesFoundation/talawa-api/blob/62d6dc4/src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts#L18)

## Functions

### transformToDefaultGraphQLConnection

▸ **transformToDefaultGraphQLConnection**\<`T0`, `T1`, `T2`\>(`«destructured»`): [`DefaultGraphQLConnection`](utilities_graphQLConnection_generateDefaultGraphQLConnection.md#defaultgraphqlconnection)\<`T2`\>

This function is used to transform a list of objects to a standard graphQL connection object.

#### Type parameters

| Name | Type |
| :------ | :------ |
| `T0` | `T0` |
| `T1` | extends `Object` |
| `T2` | `T2` |

#### Parameters

| Name | Type |
| :------ | :------ |
| `«destructured»` | [`TransformToDefaultGraphQLConnectionArguments`](utilities_graphQLConnection_transformToDefaultGraphQLConnection.md#transformtodefaultgraphqlconnectionarguments)\<`T0`, `T1`, `T2`\> |

#### Returns

[`DefaultGraphQLConnection`](utilities_graphQLConnection_generateDefaultGraphQLConnection.md#defaultgraphqlconnection)\<`T2`\>

**`Remarks`**

The logic used in this function is common to almost all graphQL connection creation flows,
abstracting that away into this function lets developers use a declarative way to create the
graphQL connection object they want and prevents code duplication.

**`Example`**

```ts
const [objectList, totalCount] = await Promise.all([
  User.find(filter)
    .sort(sort)
    .limit(limit)
    .exec(),
  User.find(filter)
    .countDocuments()
    .exec(),
]);

return transformToDefaultGraphQLConnection\<
 String,
 DatabaseUser,
 DatabaseUser
\>(\{
 objectList,
 parsedArgs,
 totalCount,
\});
```

#### Defined in

[src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts:53](https://github.com/PalisadoesFoundation/talawa-api/blob/62d6dc4/src/utilities/graphQLConnection/transformToDefaultGraphQLConnection.ts#L53)
