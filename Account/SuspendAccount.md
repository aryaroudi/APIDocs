{{{
  "title": "SuspendAccount",
  "date": "2-14-2013",
  "author": "Richard Seroter",
  "attachments": []
}}}

Disable an existing account in the Tier 3 system. Calls to this operation must include an authorization cookie acquired from the <a href="http://help.tier3.com/entries/20339862-logon">Logon operation.</a>

## URL

    REST: https://api.tier3.com/REST/Account/SuspendAccount/&lt;format&gt; (format = XML | JSON)
    SOAP: https://api.tier3.com/SOAP/Account.asmx?op=SuspendAccount

## Request
### Attributes
<table>
  <tbody>
    <tr>
      <td><strong>Name</strong>
      </td>
      <td><strong>Type</strong>
      </td>
      <td><strong>Description</strong>
      </td>
      <td><strong>Required</strong>
      </td>
    </tr>
    <tr>
      <td>AccountAlias</td>
      <td>String</td>
      <td>Four character account alias.</td>
      <td>Yes</td>
    </tr>
  </tbody>
</table>

### Examples
<h4>JSON (REST)</h4>
<pre>{ <br />    "AccountAlias": "1000"<br />}</pre>
<h4>XML (REST)</h4>
<pre>&lt;AccountStatusRequest&gt;<br />     &lt;AccountAlias&gt;1000&lt;/AccountAlias&gt;<br />&lt;/AccountStatusRequest&gt;</pre>
<h4>XML (SOAP)</h4>
<pre>&lt;soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 

        xmlns:xsd="http://www.w3.org/2001/XMLSchema" 

        xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"&gt;

  &lt;soap:Body&gt;

    &lt;SuspendAccount xmlns="http://www.tier3.com/"&gt;

      &lt;request&gt;

         &lt;AccountAlias&gt;1000&lt;/AccountAlias&gt;

      &lt;/request&gt;

    &lt;/SuspendAccount&gt;

  &lt;/soap:Body&gt;

&lt;/soap:Envelope&gt;  

</pre> 

## Response
### Attributes
<table>
  <tbody>
    <tr>
      <td><strong>Name</strong>
      </td>
      <td><strong>Type</strong>
      </td>
      <td><strong>Description</strong>
      </td>
    </tr>
    <tr>
      <td>Success</td>
      <td>Boolean</td>
      <td>True if the request was successful, otherwise False.</td>
    </tr>
    <tr>
      <td>Message</td>
      <td>String</td>
      <td>A description of the result. The contents of this field does not contain any actionable information, it is purely intended to provide a human readable description of the result.</td>
    </tr>
    <tr>
      <td>StatusCode</td>
      <td>Int</td>
      <td>This value will help to identify any errors which were encountered while processing the request. The value of '0' indicates success, all non-zero StatusCodes indicate an error state.</td>
    </tr>
    <tr>
      <td>RequestID</td>
      <td>Int</td>
      <td>The ID of the Queued request.Status of the request can be obtained by calling the&nbsp;<a href="http://help.tier3.com/entries/20561586-get-deployment-status">GetDeploymentStatus</a>&nbsp;method.</td>
    </tr>
  </tbody>
</table>

### Examples
<h4>JSON (REST)</h4>
<pre>{

  "Success": true,

  "Message": "Account Suspended.",

  "StatusCode": 0,

  "RequestID": 100

}</pre>
<h4>XML (REST)</h4>
<pre>&lt;QueuedItemResponse Success="true" Message="Account Suspended." StatusCode="0"&gt;

    &lt;RequestID&gt;100&lt;/RequestID&gt;

&lt;/QueuedItemResponse&gt;</pre>
<h4>XML (SOAP)</h4>
<pre>&lt;soap:Envelope xmlns:soap="http://www.w3.org/2003/05/soap-envelope" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"&gt;

&lt;soap:Body&gt;

    &lt;SuspendAccountResponse xmlns="http://www.tier3.com/"&gt;

    &lt;QueuedItemResponse Success="true" Message="Account Suspended." StatusCode="0"&gt;

        &lt;ResponseID&gt;100&lt;/ResponseID&gt;

    &lt;/QueuedItemResponse&gt;

&lt;/SuspendAccountResponse&gt;

&lt;/soap:Body&gt;

&lt;/soap:Envelope&gt;
</pre>

### Status Codes
<table>
  <tbody>
    <tr>
      <td><strong>Status Code</strong>
      </td>
      <td><strong>Description</strong>
      </td>
    </tr>
    <tr>
      <td>0</td>
      <td>Request was successfully processed</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Unknown Error. &nbsp;An application error occurred processing your request, contact Tier3 support to resolve the issue.</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Resource Not Found. &nbsp;Provided account alias does not exist.</td>
    </tr>
    <tr>
      <td>100</td>
      <td>Authentication Failed. &nbsp;You must logon to the API prior to calling this method.</td>
    </tr>
    <tr>
      <td>1600</td>
      <td>Account Alias Required. &nbsp;You must provide an account alias when calling this method.</td>
    </tr>
  </tbody>
</table>