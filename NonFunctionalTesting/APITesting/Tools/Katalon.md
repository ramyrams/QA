# test API with Katalon Studio

# API For Practice
https://reqres.in/
http://jsonpath.com/
https://prnt.sc/


# JSON for Import
https://petstore.swagger.io/v2/swagger.json
https://petstore.swagger.io/
https://petstore.swagger.io/


https://docs.katalon.com/katalon-studio/videos/debug_automation_scripts_katalon_studio.html
https://github.com/katalon-studio-samples
https://docs.katalon.com/katalon-studio/videos/perform_api_testing_katalon_studio.html
https://docs.katalon.com/katalon-studio/docs/assert-statements.html
https://docs.katalon.com/katalon-studio/tutorials/connect_db_gui_testing.html


https://help.testlodge.com/hc/en-us/articles/226734968-API-Test-cases

https://docs.katalon.com/katalon-studio/videos/create_environment_profile.html

Katalon Studio 18 - How to test API with Katalon Studio
https://www.youtube.com/watch?v=Evikp4eQSGs


https://www.youtube.com/watch?v=xBjNhauVDio&list=PLhW3qG5bs-L_D4ZePNNjvmIULuu6mBHbu


https://www.youtube.com/watch?v=0nyUqIrQLBY

https://www.youtube.com/watch?v=aqrxDxumKZQ


# Sample
https://github.com/katalon-studio-samples/jira-api-tests


# Code Snippet
https://forum.katalon.com/discussion/5259/how-to-set-http-header-with-variable

```groovy



### Parsing JSON response using groovy

import groovy.json.*

def json = '''[ 
    { "name": "John", "start_date": "2016-09-30", "sort_order": 1 },
    { "name": "Tony", "start_date": "2016-06-30", "sort_order": 2 } ]'''

def parsed = new JsonSlurper().parseText(json)

assert parsed.name == ['John', 'Tony']


### JsonSlurper
JsonSlurper slurper = new JsonSlurper()
Map parsedJson = slurper.parseText(jsonString)

### Get a Key Value
String idValue = parsedJson.menu.id
String idValue2 = parsedJson.get("menu").get("id")


### Verify if a Key Is Present in JSON

import com.kms.katalon.core.util.KeywordUtil

String getSelectedKey = parsedJson.menu.id

if(getSelectedKey == null) {
	KeywordUtil.markFailed("Key is not present")
}


//It is a simple check for the null — if the given key is not found, null is returned. But, there is one special case when this code won’t work, that is, if key “id” has value null in your JSON. For such cases, you should use more robust code:
boolean isKeyPresent = parsedJson.get("menu").keySet().contains("id")

if (!isKeyPresent) {
	KeywordUtil.markFailed("Key is not present")
}

## Get an Array Element

String idValue = parsedJson.menu.tools.actions[0].title
String idValue2 = parsedJson.get("menu").get("tools").get("actions").get(0).get("title")


### Get an Array Element Based on Some Condition


def array1 = parsedJson.menu.tools.actions
String onlickValue1 = ""
for(def member : array1) {
      if(member.id == 'Open') {
      onlickValue1 = member.title
      break
      }
}




TestObjectProperty header4 = new TestObjectProperty("Cookie", ConditionType.EQUALS, "anyCookieHere")

v


//get data
def data = findTestData('Data Files/DB Data')
// Get specific data (column, row) as a variable
String record = data.getValue(3, 4)
//print my variable
println record


//https://docs.katalon.com/katalon-studio/docs/common-call-test-case.html
'Use WS keyword'
WS.callTestCase(findTestCase('DDR_NavigateToPageThenVerifyPageTitle'), ['p_Protocol' : null, 'p_DomainName' : null, 'p_Path' : null, 'p_WindowTitle' : null])
WS.callTestCase(null, null, FailureHandling.STOP_ON_FAILURE)

//'Concatenate all strings end-to-end into one string.'
//https://docs.katalon.com/katalon-studio/docs/common-concatenate.html
WS.concatenate(['Katalon', 'Automation Tool'] as String[], FailureHandling.STOP_ON_FAILURE)
WS.concatenate(null, FailureHandling.STOP_ON_FAILURE)

'Verify if response object contains email@katalon.com value'
//https://docs.katalon.com/katalon-studio/docs/ws-contains-string.html
WS.containsString(resObj, 'email@katalon.com', false)
WS.containsString(apiReesponse, responseText, false, FailureHandling.STOP_ON_FAILURE)


//https://docs.katalon.com/katalon-studio/docs/common-delay.html
//You want to delay the execution for 10 seconds.
WS.delay(10)
WS.delay(responseText, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/ws-send-request.html#example
//'Send a SOAP request and returns its response'
def response = WS.sendRequest(findTestObject('SOAP_ConvertWeight'))
WS.sendRequest(null, FailureHandling.STOP_ON_FAILURE)

WS.sendRequestAndVerify(null);
WS.sendRequestAndVerify(null, FailureHandling.STOP_ON_FAILURE)

//'Verify if checked data of checkpoint matches their source data.'
//https://docs.katalon.com/katalon-studio/docs/common-verify-checkpoint.html
WS.verifyCheckpoint(findCheckpoint('Checkpoints/chk_DataSnapshot'), false)
WS.verifyCheckpoint(null, false, FailureHandling.STOP_ON_FAILURE)

'Verify if comment\'s email after sending request is correct or not'
//https://docs.katalon.com/katalon-studio/docs/ws-verify-element-property-value.html
WS.verifyElementPropertyValue(response, '[0].email', 'Eliseo@gardner.biz')
WS.verifyElementPropertyValue(apiReesponse, responseText, responseText, FailureHandling.STOP_ON_FAILURE)

//'Verify number of expected employee contact records'
//https://docs.katalon.com/katalon-studio/docs/ws-verify-elements-count.html
WS.verifyElementsCount(resObj, 'employee.contacts', 3)
WS.verifyElementsCount(apiReesponse, responseText, 0, FailureHandling.STOP_ON_FAILURE)

'Verify converted weight after sending request is correct or not'
//https://docs.katalon.com/katalon-studio/docs/ws-verify-element-text.html
WS.verifyElementText(response, 'ConvertWeightResult', '3000')
WS.verifyElementText(apiReesponse, responseText, responseText, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/common-verify-equal.html
//Verify if two objects are equal.
WS.verifyEqual(10, 10)
WS.verifyEqual(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)


https://docs.katalon.com/katalon-studio/docs/common-verify-greater-than.html
//Verify if the actual number is greater than the expected number.
WS.verifyGreaterThan(apiReesponse, responseText)
WS.verifyGreaterThan(12, 10)
WS.verifyGreaterThan(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)

https://docs.katalon.com/katalon-studio/docs/common-verify-greater-than-or-equal.html
WS.verifyGreaterThanOrEqual(apiReesponse, responseText)
WS.verifyGreaterThanOrEqual(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/common-verify-less-than.html
WS.verifyLessThan(apiReesponse, responseText)
WS.verifyLessThan(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/common-verify-less-than-or-equal.html
WS.verifyLessThanOrEqual(apiReesponse, responseText)
WS.verifyLessThanOrEqual(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/common-verify-match.html
WS.verifyMatch(responseText, responseText, false)
WS.verifyMatch('Katalon', '(K|T)atalon', true)
WS.verifyMatch(responseText, responseText, false, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/common-verify-not-equal.html
WS.verifyNotEqual(apiReesponse, responseText)
WS.verifyNotEqual(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)

//https://docs.katalon.com/katalon-studio/docs/common-verify-not-match.html
WS.verifyNotMatch(responseText, responseText, false)
WS.verifyNotMatch('Katalon', '(L|T)atalon', true)
WS.verifyMatch(responseText, responseText, false, FailureHandling.STOP_ON_FAILURE)

WS.verifyNotEqual(apiReesponse, responseText)
WS.verifyNotEqual(apiReesponse, responseText, FailureHandling.STOP_ON_FAILURE)

WS.verifyNotMatch(responseText, responseText, false)
WS.verifyNotMatch(responseText, responseText, false, FailureHandling.STOP_ON_FAILURE)

'Verify if the response from "REST_Status Codes/POST_201" object returns the 201 status code'
//https://docs.katalon.com/katalon-studio/docs/ws-verify-response-status-code.html
WS.verifyResponseStatusCode(response, 201)


/*FailureHandling.STOP_ON_FAILURE
FailureHandling.CONTINUE_ON_FAILURE
FailureHandling.OPTIONAL
*/
//WS.verifyResponseStatusCode(apiReesponse, 0, FailureHandling.STOP_ON_FAILURE)


//https://docs.katalon.com/katalon-studio/docs/ws-verify-response-status-code-in-range.html
WS.verifyResponseStatusCodeInRange(apiReesponse, 0, 0)
WS.verifyResponseStatusCodeInRange(apiReesponse, 0, 0, FailureHandling.STOP_ON_FAILURE)



println object.get("applications").get(0).get("id")



def responseDataGenres = WS.sendRequest(findTestObject('Object Repository/APIs/_(api)_genres'))
responseText = responseDataGenres.getResponseText()
def parsed = new JsonSlurper().parseText(responseText)
assert parsed.franchises[0].genres*.find { 'comedy' in it.value }.key.size() == 1


import groovy.json.JsonOutput
import groovy.json.JsonSlurper

def text = '''
{"applications":[
{"name":"test123","id":"c1257c5","description":"test","type":"generic","version":"0.1"},
{"name":"Asset_1","id":"a9e0bce","description":"sfsdgdg","type":"generic","version":"0.1"},
{"name":"Asset_2","id":"a9e0cd2","description":"sffgdgf","type":"generic","version":"0.1"}
]
}
'''
println JsonOutput.prettyPrint(text)

def jsonSlurper = new JsonSlurper()
def object = jsonSlurper.parseText(text)
assert object.applications[0].id == 'c1257c5'
assert object.applications[1].id == 'a9e0bce'
assert object.applications[2].id == 'a9e0cd2'


import groovy.json.JsonSlurper

def json = new JsonSlurper().parseText('{"applications":[{"name":"test123","id":"c1257c5","description":"test","type":"generic","version":"0.1"},{"name":"Asset_1","id":"a9e0bce","description":"sfsdgdg","type":"generic","version":"0.1"},{"name":"Asset_2","id":"a9e0cd2","description":"sffgdgf","type":"generic","version":"0.1"}]}')

println(json.applications[1].id)





com.kms.katalon.core.testobject.RequestObject ro = findTestObject('Object Repository/yourRestDefinition')
ro.setRestUrl("whatever you want")

basicaly you can build your own object from scratch ... just check api for RequestObject



response = WS.sendRequest(reqObj)
println response.getHeaderFields()['Set-Cookie']



 def slurper = new groovy.json.JsonSlurper()
 def result = slurper.parseText('{"person":{"name":"Guillaume","age":33,"pets":["dog","cat"]}}')

 assert result.person.name == "Guillaume"
 assert result.person.age == 33
 assert result.person.pets.size() == 2
 assert result.person.pets[0] == "dog"
 assert result.person.pets[1] == "cat"
 
 
 println object.get("applications").get(0).get("id")
 
 
 See the code below:
def data = findTestData("Policy/Member")

def NovaWrapperWebApi = MapWebApiBodyVariables(index)
def response = WS.sendRequest(NovaWrapperWebApi)
def memberIdNumber = findTestData('Policy/Member').getValue('IDNumber', index);
GlobalVariable.result = 'Row number '+index+' '+response.getResponseText()'
System.out.println(GlobalVariable.result)



Curly braces inside URI request
https://forum.katalon.com/discussion/9433/curly-braces-inside-uri-request


Dynamic base URL in Test Object (take it from environment profile)


def responseData = WS.sendRequest(findTestObject('OR/WsObject',[('acctNum'): accountNumber]))



import org.apache.commons.lang.RandomStringUtils

String charset = (('A'..'Z') + ('0'..'9')).join()
Integer length = 9
def randomString = RandomStringUtils.random(length, charset.toCharArray())

println randomString

{
  "key": “${keyValue}”,
  “userName": “dave”,
  “country”: “GB”
}

response = WS.sendRequest(findTestObject('pathInObjectRepository/requestObject',[('keyValue'): randomString]))


r if you want a random int, the below line would give you a int between 999999 and 1000000.

int randomInt = Math.abs(new Random().nextInt()) % 999999 + 1000000




@Keyword
def randomString(int stringLength) {
String charset = (('A'..'Z') + ('0'..'9')).join()
Integer length = stringLength
def randomString = RandomStringUtils.random(length, charset.toCharArray())
return randomString
}





@Keyword
def PATCH(String URL, String Identifier, String JSONBody) {

OkHttpClient client = new OkHttpClient()

MediaType mediaType = MediaType.parse("application/json")

String url = URL + '/' + Identifier

String requestBody = JSONBody

RequestBody body = RequestBody.create(mediaType, requestBody)

Request request = new Request.Builder()
.url(url)
.patch(body)
.addHeader("content-type", "application/json")
.addHeader("cache-control", "no-cache")
.build();

Response response = client.newCall(request).execute()

String responseBodyString = response.body().string()

//Create a new jsonSlurper object to manipulate the response from the API
JsonSlurper jsonSlurper = new JsonSlurper()

//Create a new object which will represent the response data from the API
def responseObject = jsonSlurper.parseText(responseBodyString)

return responseObject

}
}


import org.openqa.selenium.Cookie

Cookie myCookie = new Cookie("TokenNameYouNeedSet", tokenFromFirstRequest)
response = WS.sendRequest(findTestObject(requestObject.getObjectId(),[('COOKIE'): myCookie]))



@BeforeTestCase
def infoBeforeTestCase(TestCaseContext testCaseContext) {
       println testCaseContext.getTestCaseId()
}



WebUI.comment("${this.getTestCaseId()}")




try{
	response = WS.sendRequest(findTestObject('Object Repository/__Sandbox/rObject1'))
} catch (Exception ce){
	println '**********************************'
	println ce
	println '**********************************'
}


response = WS.sendRequest(findTestObject('requestObject',[('variable'): value]))


def token = response.getHeaderFields().token
Cookie myCookie = new Cookie("token", token)
newResponse = WS.sendRequest(findTestObject(ro.getObjectId(),[('COOKIE'): myCookie]))





import groovy.json.JsonSlurper

def slurper = new groovy.json.JsonSlurper()
def jsonDefText = '{ "name": "John", "surname": "Doe", "options" :[{"setOption1":"valOfSetOption1_1", "setOption2":"valOfSetOption2_1","setOption3":"valOfSetOption3_1"},{"setOption1":"valOfSetOption1_2", "setOption2":"valOfSetOption2_2"}]}'  

def jsonVar = slurper.parseText(jsonDefText)

println jsonVar 

assert jsonVar.name == "John"
assert jsonVar.options[0].setOption1 == "valOfSetOption1_1"
assert jsonVar.options[1].setOption2 == "valOfSetOption2_2"
try{
	assert jsonVar.options[1].setOption3 == "valOfSetOption3_2"
} catch (org.codehaus.groovy.runtime.powerassert.PowerAssertionError pae){
	println pae
	println "There is no such element as: jsonVar.options[2].setOption3"
}
jsonVar.options[1].setOption3 = "valOfSetOption3_2"
try{
	assert jsonVar.options[1].setOption3 == "valOfSetOption3_2"
} catch (org.codehaus.groovy.runtime.powerassert.PowerAssertionError pae){
	println pae
	println "There is no such element as: jsonVar.options[2].setOption3"
}



import internal.GlobalVariable
import groovy.json.JsonSlurper

GlobalVariable.yourTokenVar = Token 

def jsonSlurper = new JsonSlurper()
def res = jsonSlurper.parseText(response.getResponseText())
AutToken = res.bearer_token
WS.verifyResponseStatusCode(response, 200)




TestObjectProperty auth = new TestObjectProperty()
auth.setName("Authorization")
auth.setValue("Bearer " + token)
TestObjectProperty content = new TestObjectProperty()
content.setName("Content-Type")
content.setValue("text/xml")
 
def headers = new ArrayList()
headers.add(auth)
headers.add(content)
TestObjectProperty param = new TestObjectProperty()
param.setName("--data")
param.setValue("@/path/to/JUnit_Report.xml")
def params = new ArrayList()
params.add(param)
 
RequestObject reqObj = new RequestObject()
reqObj.setHttpHeaderProperties(headers)
reqObj.setRestRequestMethod('POST')
reqObj.setRestUrl('https://host/api/v1/import/execution/junit?projectKey=XXX')
reqObj.setRestParameters(params)
def getResponse = WSBuiltInKeywords.sendRequest(reqObj)
println(AutToken)
GlobalVariable.AutToken = AutToken



String lines = '{"StudentList": [{"studentId": "1234","name": "abc","state": "S1247","city": "Chennai","zipCode": "686667","createdBy": "test user"},{"studentId": "5679","name": "ced","state": "S1233","city": "Bangalore","zipCode": "560075","createdBy": "test user"},{"studentId": "7899","name": "teud","state": "S1233","city": "Bangalore","zipCode": "560075","createdBy": "test user"}]}'

Map resp = new JsonSlurper().parseText(lines)

ArrayList details = resp.get("StudentList")

for(Map oneStud in details) {
	println oneStud.get("name")
}




https://docs.katalon.com/katalon-studio/tutorials/parse_json_responses.html

def response = WS.sendRequest(findTestObject('REST_CommentDetails')) 
headerFields = response.getHeaderFields()
println headerFields['Set-Cookie']


def a = WS.sendRequest(findTestObject('New_Request_Auth', ['email' : 'sgappfr2@vpmel.fr', 'password' : 'azerty!!']))

request.addProperty('WSS-Password Type', ConditionType.EQUALS, 'PasswordText')


https://mrhaki.blogspot.com/2011/11/grassroots-groovy-reading-json-with.html


'Create a new POST object using builder'
def builder = new RestRequestObjectBuilder()
def reqOrders = builder
	.withRestRequestMethod('POST')
	.withRestUrl('URL')
	.withHttpHeaders([
		new TestObjectProperty('Authorization', ConditionType.EQUALS, parsedUserToken),
		new TestObjectProperty('Content-Type', ConditionType.EQUALS, 'application/json')
	])
	.withRestParameters([
		new TestObjectProperty('service', ConditionType.EQUALS, 'value'),
		new TestObjectProperty('userId', ConditionType.EQUALS, 'value'),
		new TestObjectProperty('currency', ConditionType.EQUALS, 'value'),
		new TestObjectProperty('price', ConditionType.EQUALS, 'value'),
		new TestObjectProperty('amount', ConditionType.EQUALS, 'value'),
		new TestObjectProperty('coins', ConditionType.EQUALS, 'value'),
		new TestObjectProperty('lang', ConditionType.EQUALS, 'EN'),
		new TestObjectProperty('returnPage', ConditionType.EQUALS, 'value')
	])
	.build()
'Send a request'
def respOrders = WSBuiltInKeywords.sendRequest(reqOrders)



RequestObject requestObj = new RequestObject() 
List<TestObjectProperty> headerParameters = new ArrayList() 

//adding the header params
headerParameters.add(new TestObjectProperty('Content-Type', 
ConditionType.EQUALS, 'application/vnd.api+json'))
headerParameters.add(new TestObjectProperty('session_id', ConditionType.EQUALS, 'xxxxx'))

requestObj.setHttpHeaderProperties(headerParameters)
requestObj.setRestUrl("url")
requestObj.setRestRequestMethod("POST")

WS.sendRequest(requestObj) 





import com.kms.katalon.core.testobject.TestObjectProperty

import com.kms.katalon.core.testobject.ConditionType

'Get token'
String token = WebUI.callTestCase(findTestCase('API/Authentication'), [:], FailureHandling.CONTINUE_ON_FAILURE)

'Scope to a project'
RequestObject ScopeToProject = findTestObject('API/ScopeToProject')

'Create new ArrayList'
ArrayList<TestObjectProperty> HTTPHeader = new ArrayList<TestObjectProperty>()

'Send token in HTTP header'
HTTPHeader.add(new TestObjectProperty('X-Auth-Token', ConditionType.EQUALS, token))

'Set that token'
ScopeToProject.setHttpHeaderProperties(HTTPHeader)




https://github.com/alexdeleon/groovy-json-schema




//How to verify Array in Api Resful

def jsonSlurper = new JsonSlurper()
def res = jsonSlurper.parseText(response.getResponseText())
println(res.errors.message[0])



import groovy.json.JsonSlurper 

class Example {
   static void main(String[] args) {
      def jsonSlurper = new JsonSlurper()
      def object = jsonSlurper.parseText('{ "name": "John", "ID" : "1"}') 
		
      println(object.name);
      println(object.ID);
   } 
}


//How to get size of element in API Response

def results = new groovy.json.JsonSlurper().parseText( response.getResponseBodyContent() )
println results.size()

'Get response text'

response = WS.sendRequest(ScopeToProject)

'Verify if scope to project was successfull'
WS.verifyElementPropertyValue(response, 'data.currentProject', 'ab8e52e92deb459596e3911f9f09934c')



import groovy.json.JsonSlurper
responseData = WS.sendRequest(findTestObject("POST RESTFUL"));
responseText = responseData.getResponseText();
def json = new JsonSlurper().parseText(responseText)
println json.results.size();





import com.kms.katalon.core.testobject.RequestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS

import groovy.json.JsonSlurper

// create a new instance of JsonSlurper
JsonSlurper parser = new JsonSlurper()

// build first RequestObject
RequestObject ro = new RequestObject("x")
ro.setRestRequestMethod("GET")
ro.setRestUrl("https://s3.amazonaws.com/postman-static-getpostman-com/postman-docs/test_data_file.json")

// send request and get response text
def resp = WS.sendRequest(ro).getResponseText()
// parse response text as JSON
def parsedResp = parser.parseText(resp)

// get parameter you need from JSON response - parse it using dot notation
def param = parsedResp.username[0]

// build a second request and pass a param from 1st request
RequestObject ro2 = new RequestObject("y")
ro2.setHttpBody(param)
ro2.setRestUrl("www.yoururl.com")

WS.sendRequest(ro2)


https://gist.github.com/executeautomation/72292183031b45e70445d27593d55e2c

//POST object
def request = (RequestObject)findTestObject('POST')
String body = '{ "id": 20, "title": "Appiums", "author": "Karthik KK"}'

try{
	request.setBodyContent(new HttpTextBodyContent(body,"UTF-8", "application/json"))
}
catch(Exception ex){
	println (ex.detailMessage)
}
//Make POST request
WS.sendRequest(request)

//Verify response with GET
def response = (RequestObject)findTestObject('GET')

List<TestObjectProperty> params = new ArrayList();
params.add(new TestObjectProperty("id", ConditionType.EQUALS, "20"))
response.setRestParameters(params)

//Make GET Request
def result = WS.sendRequest(response)
//Verify title from response
WS.verifyElementPropertyValue(result, "title[0]", "Appiums", FailureHandling.STOP_ON_FAILURE)


https://gist.github.com/executeautomation/464608d92e482c87a8772a9680588f80
def response = WS.sendRequest(findTestObject('GetEAPosts', [('') : 3]))
WS.verifyElementPropertyValue(response, '[2].title', 'Katalon Studio', FailureHandling.STOP_ON_FAILURE)
//Post
def response1 = WS.sendRequest(findTestObject('GetEAPosts'))
WS.verifyResponseStatusCode(response1, 200, FailureHandling.STOP_ON_FAILURE)
//Post to get element count
WS.verifyElementsCount(response1, '[2].title', 14)

//http://mundrisoft.com/tech-bytes/read-data-from-excel-sheet-using-katalon-studio/
url = findTestData(“New Test Data”).getValue(“url”, 1)
```
