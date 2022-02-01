# Categories

> This page is under construction. User API v2 is in beta and is subject to change.

## List Categories

### *GET* https://ed.link/api/v2/my/classes/:class\_id/categories

Retrieve a list of **[Categories](../models/external/category)** for a given class.

#### Request Parameters

This query allows for [standard paging parameters](../../../guides/v2.0/paginated-requests).

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/classes/${class_id}/categories`, {
  headers: {
    authorization: `Bearer ${person_access_token}`
  }
})
```

#### Sample Response

```json
{
  "$request": "00000000-0000-0000-0000-000000000000",
  "$data": [
    {
      "title": "Example Category",
      "updated_date": "2021-12-27T18:53:45.077Z",
      "id": "00000000-0000-0000-0000-000000000000"
    }
  ],
  "$count": 1
}
```

## Fetch Category 

### *GET* https://ed.link/api/v2/my/classes/:class\_id/categories/:category\_id

Retrieve information about a specific **[Category](../models/external/category)**.

#### Request Parameters

| Parameter     | Type     | Description                                                          |
|---------------|----------|----------------------------------------------------------------------|
| `class_id`    | `string` | The UUID of the desired **[Class](../models/external/class)**.       |
| `category_id` | `string` | The UUID of the desired **[Category](../models/external/category)**. |

#### Sample Request

```javascript
axios.get(`https://ed.link/api/v2/my/classes/${class_id}/categories/${category_id}`, {
	headers: {
		authorization: `Bearer ${person_access_token}`
	}
});
```

#### Sample Response

```json
{
  "$data": {
    "title": "Example Category",
    "updated_date": "2021-12-27T18:53:45.077Z",
    "id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```

## Create Category

### *POST* https://ed.link/api/v2/my/classes/:class\_id/categories

Create a new **[Category](../models/external/category)** in the given **[Class](../models/external/class)**.

The user must be enrolled as a `teacher`, `ta`, `designer`, `administrator`, or `district-administrator` in the class to use this endpoint.

#### Request Parameters

| Parameter  | Type     | Description                                                    |
|------------|----------|----------------------------------------------------------------|
| `class_id` | `string` | The UUID of the desired **[Class](../models/external/class)**. |

#### Request Body

The request body should contain an **[Category](../models/external/category)** object.

The following fields are allowed: `title`, `weight`, `drop_lowest`, `position`.

The following fields are required: `title`.

```json
{
  "title": "Example Category",
  "position": 2
}
```

#### Sample Response

The response contains the newly created **[Category](../models/external/category)** object.

```json
{
  "$data": {
    "title": "Example Category",
    "position": 2,
    "updated_date": "2021-12-27T18:53:45.077Z",
    "id": "00000000-0000-0000-0000-000000000000"
  },
  "$request": "00000000-0000-0000-0000-000000000000"
}
```
