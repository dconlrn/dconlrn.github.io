---
mermaid: true
---



## SCRIPT INTERACTION FLOW CHART


<div class="mermaid"> 


graph LR;
    A[game.cs]-->B{'stuff'};
    A-->|STUFF|C;
    B-->D;
    C-->D;


</div> 


<div class="mermaid"> 


graph LR;
    A[game.cs]-->B{stuff};
    A-->|STUFF with a space|C[TESTING];
    B-->D((circle here));
    C-->D;


</div> 

<div class="mermaid"> 


graph TD;
    A[PareidoliaNet.cs]-->B{PF_PLAYFAB.cs};
    A-->C[PF_IAP.cs];
    D[MyAdmin.cs]-->B;
    B-->|METHOD CALLAND ARGUMENTS IF REQUIRED|J[METHOD CALL PlayFabAdminAPI.'MethodName'];
    J-->|GENERAL STRUCTURE OF ARGUMENTS|L((new 'MethodNameRequest'ie. PlayFabId VAR Response Result Error Lambda));
    B-->|METHOD CALLAND ARGUMENTSIF REQUIRED|K[METHOD CALL PlayFabClientAPI.'MethodName'];
    K-->|GENERAL STRUCTURE OF ARGUMENTS|L;
    L-->|METHOD CALL|E[PlayFabAdminAPI.cs];
    L-->|METHOD CALL|F[PlayFabClientAPI.cs];
    E[PlayFabAdminAPI.cs]-->G[PlayFabAdminModels.cs];
    F[PlayFabClientAPI.cs]-->H[PlayFabClientModels.cs];
    G-->|CALL CONVERTED TO  API REQUEST|g[PlayFabHttp.MakeApiCall];
    H-->|CALL CONVERTED TO  API REQUEST|g;
    C[PF_IAP.cs]-->I[Unity.EnginePurchasing];

</div> 

## PLAYFAB API NAMESPACE METHOD CALL EXAMPLE

-------------------------------

{% highlight java %}


     public void REGISTER(string username, string emailAddress, string password)
   {   // ACCESING THE PLAYFABCLIENTAPI NAMESPACE
        PlayFabClientAPI.RegisterPlayFabUser(// ACCESSING A METHOD IN THE NAMESPACE "REGISTERPLAYFABUSER"
           // SENDING THE REQUIRED PARAMETERS FOR THE METHOD TO WORK
           // THE "new" REQUEST METHOD IS PART OF THE APICLIENTMODELS NAMESPACE
           // IT IS GOING TO STRUCTURE THE HEADER OF OUR API REQUEST FOR US
            new RegisterPlayFabUserRequest()
            {
                Email = emailAddress,
                Password = password,
                Username = username,
                RequireBothUsernameAndEmail = true
            },
            response =>
            {
                // The thing to notify the user that a new account has been created successfully
                
                Debug.Log($"Account created friend! : {username}, {emailAddress}");
            },
            error =>
            {
                Debug.Log($"Account not created am sad! : {username}, {emailAddress} \n {error.ErrorMessage}");
            }
        );
    }


{% endhighlight %}

## ONCE THIS METHOD IS CALLED ALL OF THIS STUFF GETS SENT TO THE API NAMESPACE METHOD

---------------------------


{% highlight java %}

// THE PlayFabUserRequest ARGUMENT GENERATES A HEADER BASED ON THE PARAMETERS WE PUT IN IT FROM THE FUNCTION CALL IN THE ABOVE CODE BLOCK WHICH WAS IN A DIFFERENT NAMESPACE. IT ALSO AUTOMATICALLY RETURNS THE TITLEID AND AUTHENTICATION CREDENTIALS, PROVIDED PLAYFAB WAS SETUP PROPERLY, THAT WILL MAKE THE API WORK.
       
//NOTE: The PlayFabUserRequest argument is also a seperate namespace part of the ClientModels namespace in this ex.
        public static void RegisterPlayFabUser(RegisterPlayFabUserRequest request, Action<RegisterPlayFabUserResult> resultCallback, Action<PlayFabError> errorCallback, object customData = null, Dictionary<string, string> extraHeaders = null)
         {
            var context = (request == null ? null : request.AuthenticationContext) ?? PlayFabSettings.staticPlayer;
            var callSettings = PlayFabSettings.staticSettings;
            request.TitleId = request.TitleId ?? callSettings.TitleId;

// THIS IS THE PART THAT MAKES THE ACTUAL API REQUEST
 
            PlayFabHttp.MakeApiCall("/Client/RegisterPlayFabUser", request, AuthType.None, resultCallback, errorCallback, customData, extraHeaders, context, callSettings);
        }

{% endhighlight %}







**The online documentation is not the best but lets take a look at it anyway hopefully it makes much more sense now**

## Request Header

<table class="" aria-label="Table 1">
<tbody><tr>
  <th class="">Name</th>
  <th class="">Required</th>
  <th class="">Type</th>
  <th class="">Description</th>
</tr>
<tr>
<td>
None
</td>
<td>
  True
</td>
<td>
<td>
string
</td>
<td>	This API requires no authentication headers (usually provides one to other calls).
</td>
</tr>
</tbody>
</table>

**Request Body**

<div class=""><table class="" aria-label="Table 2">
<tbody>
<tr>
<th class="">Name</th>
<th class="">Required</th>
<th class="">Type</th>
<th class="">Description</th>
</tr>
<tr>
<td>
TitleId
</td>
<td>
True
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>Unique identifier for the title, found in the Settings &gt; Game Properties section of the PlayFab developer site when a title has been selected.</p>
</td>
</tr><tr>
<td>
CustomTags
</td>
<td aria-label="No value">
</td>
<td>
<p>
object
</p>
</td>
<td>
<p>The optional custom tags associated with the request (e.g. build number, external trace identifiers, etc.).</p>
</td>
</tr><tr>
<td>
DisplayName
</td>
<td aria-label="No value">
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>An optional parameter for setting the display name for this title (3-25 characters).</p>
</td>
</tr><tr>
<td>
Email
</td>
<td aria-label="No value">
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>User email address attached to their account</p>
</td>
</tr><tr>
<td>
EncryptedRequest
</td>
<td aria-label="No value">
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>Base64 encoded body that is encrypted with the Title's public RSA key (Enterprise Only).</p>
</td>
</tr><tr>
<td>
InfoRequestParameters
</td>
<td aria-label="No value">
</td>
<td>
<p>
<a href="" data-linktype="">Get<wbr>Player<wbr>Combined<wbr>Info<wbr>Request<wbr>Params</a>
</p>
</td>
<td>
<p>Flags for which pieces of info to return for the user.</p>
</td>
</tr><tr>
<td>
Password
</td>
<td aria-label="No value">
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>Password for the PlayFab account (6-100 characters)</p>
</td>
</tr><tr>
<td>
PlayerSecret
</td>
<td aria-label="No value">
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>Player secret that is used to verify API request signatures (Enterprise Only).</p>
</td>
</tr><tr>
<td>
RequireBothUsernameAndEmail
</td>
<td aria-label="No value">
</td>
<td>
<p>
boolean
</p>
</td>
<td>
<p>An optional parameter that specifies whether both the username and email parameters are required. If true, both parameters are required; if false, the user must supply either the username or email parameter. The default value is true.</p>
</td>
</tr><tr>
<td>
Username
</td>
<td aria-label="No value">
</td>
<td>
<p>
string
</p>
</td>
<td>
<p>PlayFab username for the account (3-20 characters)</p>
</td>
</tr>		</tbody></table></div>
