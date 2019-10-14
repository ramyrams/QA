# Karate

* [Karate](https://github.com/intuit/karate) - Web-Services Testing Made Simple - Opensource Github
* [New automation framework released to test APIs: Introducing Karate, by Intuit India's Peter Thomas](http://www.tjmaher.com/2017/03/new-automation-framework-released-to.html)


## Peter's Hello World Example
```java
Feature: karate 'hello world' example
Scenario: create and retrieve a cat

Given url 'http://myhost.com/v1/cats'
And request { name: 'Billie' }
When method post
Then status 201
And match response == { id: '#notnull', name: 'Billie' }

Given path response.id
When method get
Then status 200
```
## Example
Over ten demos are on the Karate Demo Page: https://github.com/intuit/karate/tree/master/karate-demo

## Video
* [Karate_ A DSL for writing web service API acceptance tests, BDD style](https://vimeo.com/209699865)
* [Karate A REST Test Tool for API testing](https://www.youtube.com/watch?v=yKRR1j0A9Q4)


Karate a Rest Test Tool – Basic API Testing
https://www.joecolantonio.com/2017/03/23/rest-test-tool-karate-api-testing/
