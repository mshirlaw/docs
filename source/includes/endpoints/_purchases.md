## Purchases

> Object URI:  
`/api/v0/purchases`

Track the purchases made when completing a [job](#jobs-projects), [issue](#issues) or [contract](#contracts). More information may be found on the [release blog](https://www.accelo.com/resources/blog/your-billing-simplified-introducing-the-new-purchases-module/).

### The Purchase Object (Beta)
The purchase object contains the following fields:

| Field | Type | Description |
|:-|:-|:-|
| **id** | unsigned | The unique identifier for the purchase. |
| **title** | string | The title of the purchase. |
| owner_id | unsigned | The identifier of the [staff](#staff) who owns the purchase. Defaults to "0". |
| creator_id | unsigned | The identifier of the [staff](#staff) who created the invoice. Defaults to "0". |
| affiliation_id | unsigned | The identifier of the [affiliation](#affiliations) associated with the purchase. Defaults to "0". |
| amount  | decimal | The monetary amount of the purchase. Defaults to "0.00".|
| tax | decimal | The tax on the purchase. Defaults to "0.00". |
| total | decimal | The total value of the purchase: `amount + tax`. Defaults to "0.00". |
| date_purchased | unix ts | The date of the purchase. Defaults to "0". |





### Get Purchase (Beta)
`GET /purchases/{purchase_id}`
> Sample request:

```http
GET /api/v0/purchases/{purchase_id} HTTP/1.1
HOST: {deployment}.api.accelo.com
Authorization: Bearer {access_token}
```

```shell
CURL -X get \
    https://{deployment}.api.accelo.com/api/v0/purchases/{purchase_id} \
    -H 'authorization: Bearer {access_token}'
```

This request returns a [purchase](#the-purchase-object-beta)) identified by its `purchase_id`.

#### Configuring the Response
This request supports requesting additional fields and linked objects from the [purchase object](#the-purchase-object-beta)) using the [`_fields`](#configuring-the-response-fields) parameter. This request also supports [breadcrumbs](#configuring-the-response-breadcrumbs).

#### Handling the Response
The response will be the [purchase](#the-purchase-object-beta)) with its default fields and any additional fields requested through `_fields`.






### List Purchases (Beta)
`GET /purchases`

```http
GET /api/v0/purchases/ HTTP/1.1
HOST: {deployment}.api.accelo.com
Authorization: Bearer {access_token}
```

```shell
CURL -X get \
    https://{deployment}.api.accelo.com/api/v0/purchases/ \
    -H 'authorization: Bearer {access_token}'
```

This request returns a list of [purchases](#the-purchase-object-beta)) on the deployment.

#### Configuring the Response

##### Pagination
This request supports all of the [pagination](#configuring-the-response-pagination) parameters.

##### Additional Fields and Linked Objects
This request also supports requesting additional fields and linked objects from the [purchase object](#the-purchase-object-beta)) using the [`_fields`](#configuring-the-response-fields) parameter, as well as [breadcrumbs](#configuring-the-response-breadcrumbs).

##### Basic Filters
This request supports the following [basic filters](#filters-basic-filters):

| Filter |
|:-|
| id |
| owner_id |
| creator_id |
| affiliation_id |

##### Date Filters
This request supports the following [date filters](#filters-date-filters):

| Filter |
|:-|
| date_purchased |

##### Order Filters
This request supports [order filters](#filters-order-filters) over the following fields:

| Field |
|:-|
| amount |
| tax |
| total |
| id |
| owner_id |
| creator_id |
| affiliation_id |

##### Range Filters
This request supports [range filters](#filters-range-filters) over the following fields:

| Field |
|:-|
| amount |
| tax |
| total |
| id |
| owner_id |
| creator_id |
| affiliation_id |

##### Searching
This request supports the [`_search`](#configuring-the-response-searching) parameter to search over teh following fields:

| Field |
|:-|
| title |

#### Handling the Response
The response will be a list of [purchases](#the-purchase-object-beta)) with their default fields and any additional fields requested through `_fields`, and displayed according to any pagination parameters, filters, or searches used.






### Count Purchases (Beta)
`GET /purchases/count`

```http
GET /api/v0/purchases/count HTTP/1.1
HOST: {deployment}.api.accelo.com
Authorization: Bearer {access_token}
```

```shell
CURL -X get \
    https://{deployment}.api.accelo.com/api/v0/purchases/count \
    -H 'authorization: Bearer {access_token}'
```

This request will return a count of [purchases](#the-purchase-object-beta)) in a list defined by any available searches or filters. With no searches or filters this will return a count of all purchases on the deployment. This request returns a single field:

| Field | Type | Description |
|:-|:-|:-|
| **count** | unsigned | A count of the purchases listed. |