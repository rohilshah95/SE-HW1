
# About Me

Name : Rohil Shah  
Unity ID: rshah8  
Student ID: 200204305


Concerns Regarding REST APIs:
* REST is stateless and all the messages exchanged between the server and client have all the context and fields concerning that message. This increases the bandwidth as there is a lot of redundant information.
* REST requests are not good for handling large amounts of data.
* REST vocabulary is not completely supported as many browsers have limited functionality for DELETE and PUT methods and many server applications don’t have support for many REST methods.
* REST APIs are generally connected to HTTP and moving it to a different protocol means restructuring the information. This makes REST non portable.
* You need to know exactly what kind of responses the REST APIs return which can be a concern while comparing it to GraphQL where the client just asks for what fields he wants.
* You need to load multiple URLs to get multiple resources instead of a single request in GraphQL.

Comparison between RESTful architecture and Graph Query Language:  
* REST has no specific tools and doesn’t matter if you use HTTP or any other protocol, while GraphQL is a specific query language which uses a single endpoint over HTTP.
* REST is designed to last while GraphQL is used for optimizing performance.
* REST control the server while GraphQL controls the data, thus making GraphQL apps fast and stable.
* In REST, the size and shape of the resource is determined by the server while, in GraphQL, the server declares the resources available and the client decides which resource it wants.
* REST APIs required loading multiple URLs to get many resources, while GraphQL can get all the resources in a single request itself, making the apps quicker on slow mobile connections. 
* REST utilizes the uniform interface of protocols like content-types and status codes in HTTP while GraphQL has its own conventions which can sometimes be confusing. 
* Although REST and GraphQL both support version evolution, version depreciation on GraphQL is very easy. This is because GraphQL users have to specify what fields do they want returned in the query. While REST returns any field in response to an API call. The developers are supposed to know about the changes in every version and what fields are there or no longer present.

Code for REST tasks: [code](https://github.ncsu.edu/rshah8/HW1/blob/master/script.js)


```js
var request = require('request');
var fs = require("fs");
var Promise = require('bluebird');
var parse = require('parse-link-header');


////// FILL IN THE BLANKS

var token = "token " + "b95f598d31265f6a5b2d9baa75c11bd1e05069eb ";
var userId = "rohilshah95";
var urlRoot = "https://api.github.com";

getYourRepos(userId);
listBranches(userId);
createRepo(userId);
createIssue(userId);
editRepo(userId);
listReactions(userId);

function getYourRepos(userName)
{

	var options = {
		url: urlRoot + '/users/' + userName + "/repos",
		method: 'GET',
		headers: {
			"User-Agent": "EnableIssues",
			"content-type": "application/json",
			"Authorization": token
		}
	};

	request(options, function (error, response, body) 
	{
		var obj = JSON.parse(body);
		console.log( obj );
		for( var i = 0; i < obj.length; i++ )
		{
			var name = obj[i].name;
			console.log( name );
		}
	});

}

function listBranches(owner)
{
	var options = {
		url: urlRoot + '/repos/' + owner + "/Twitter-Personalities"+ "/branches",
		method: 'GET',
		headers: {
			"User-Agent": "EnableIssues",
			"content-type": "application/json",
			"Authorization": token
		}
	};

	request(options, function (error, response, body) 
	{
		var obj = JSON.parse(body);
		console.log( obj );
		for( var i = 0; i < obj.length; i++ )
		{
			var name = obj[i].name;
			console.log( name );
		}
	});	
}

function createRepo(owner)
{
	var options = {
		url: urlRoot + "/user/repos",
		method: 'POST',
		json : {
			"name": "HW1",
			"homepage": "https://github.com",
			"private": false,
			"has_issues": true,
			"has_projects": true,
			"has_wiki": true
		},
		headers: {
			"User-Agent": "EnableIssues",
			"content-type": "application/json",
			"Authorization": token
		}
	};

	request(options, function (error, response, body) 
	{
		var obj = body;
		console.log( obj );
		for( var i = 0; i < obj.length; i++ )
		{
			var name = obj[i].name;
			console.log( name );
		}
	});	
}

function createIssue(userName)
{

	var options = {
		url: urlRoot + '/repos/' + userName + "/Twitter-Personalities"+ "/issues",
		method: 'POST',
		json: {"title": "bug found 2"  },
		headers: {
			"User-Agent": "EnableIssues",
			"content-type": "application/json",
			"Authorization": token
		}
	};

	request(options, function (error, response, body) 
	{
		var obj = body;
		console.log( obj );
		for( var i = 0; i < obj.length; i++ )
		{
			var name = obj[i].name;
			console.log( name );
		}
	});

}

function editRepo(owner)
{
	var options = {
		url: urlRoot + "/repos/"+owner+"/HW1",
		method: 'PATCH',
		json : {
			"name": "HW1",
			"has_issues": true,
			"has_projects": true,
			"has_wiki": true
		},
		headers: {
			"User-Agent": "EnableIssues",
			"content-type": "application/json",
			"Authorization": token
		}
	};

	request(options, function (error, response, body) 
	{
		var obj = body;
		console.log( obj );
		for( var i = 0; i < obj.length; i++ )
		{
			var name = obj[i].name;
			console.log( name );
		}
	});	
}

function listReactions(userName)
{
	var options = {
		url: urlRoot + '/repos/' + userName + "/Twitter-Personalities"+ "/issues"+"/1"+"/reactions",
		method: 'GET',
		headers: {
			"User-Agent": "EnableIssues",
			"content-type": "application/json",
			"Authorization": token,
			"Accept": 'application/vnd.github.squirrel-girl-preview'
		}
	};

	request(options, function (error, response, body) 
	{
		var obj = JSON.parse(body);
		console.log( obj );
		for( var i = 0; i < obj.length; i++ )
		{
			var name = obj[i].name;
			console.log( name );
		}
	});	
}

 
```

