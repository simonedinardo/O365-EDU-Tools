# Update educationassignment

Update the assignment object.  Only teachers in the class can do this action.  Note that the status of an assignment cannot be changed in a PATCH, the URL action should be used to change an assignment state.



Due to a bug, the graph will return educationItemBody for the instructions property.  This is an exact duplicate of the itemBody that 
is already found on the graph.   When the code moves to prodution, this will be updated.  For clients who simply use the json being
sent back and forth to the graph, there should be no work necessary to handle this change.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](../../../concepts/permissions_reference.md).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) |  EduAssignments.ReadWriteBasic, EduAssignments.ReadWrite  |
|Delegated (personal Microsoft account) |  Not supported.  |
|Application | Not supported. | 

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
PATCH /education/classes/<id>/assignments/<id>
```
## Request headers
| Header       | Value |
|:---------------|:--------|
| Authorization  | Bearer {token}. Required.  |
| Content-Type  | application/json  |

## Request body
In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|allowLateSubmissions|Boolean| Whether submisions can be submitted after the due date|
|allowStudentsToAddResourcesToSubmission|Boolean| Wether a student can add resources to a submission.  Indicated whether the only items on the submission came from the assignment resource list. |
|assignDateTime|DateTimeOffset| Date the assignmetn should be published to students. |
|assignTo|educationAssignmentRecipient| Students who get the assignment|
|displayName|String| Name of assignment. |
|dueDateTime|DateTimeOffset| Date assignment is due. |
|grading|educationAssignmentGradeType| How the assignment will be graded.|
|instructions|itemBody| Instructions to be given to the students along with the assignment. |

## Response
If successful, this method returns a `200 OK` response code and updated [educationAssignment](../resources/educationassignment.md) object in the response body.
## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "update_educationassignment"
}-->
```http
PATCH https://graph.microsoft.com/beta/education/classes/<id>/assignments/<id>
Content-type: application/json
Content-length: 279

{
  "displayName": "displayName-value",
  "instructions": {
    "contentType": "contentType-value",
    "content": "content-value"
  },
  "dueDateTime": "datetime-value"
}
```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.educationAssignment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 279

{
  "classId": "classId-value",
  "displayName": "displayName-value",
  "instructions": {
    "contentType": "contentType-value",
    "content": "content-value"
  },
  "dueDateTime": "datetime-value",
  "assignDateTime": "datetime-value",
  "assignedDateTime": "datetime-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update educationassignment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->