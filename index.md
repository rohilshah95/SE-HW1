
# About Me

Name : Rohil Shah  
Unity ID: rshah8  
Student ID: 200204305

Code for REST tasks: [code](https://github.ncsu.edu/rshah8/HW1/script.js)

```js
var request = require('request');
var fs = require("fs");
var Promise = require('bluebird');
var parse = require('parse-link-header');


////// FILL IN THE BLANKS

var token = "token " + "b95f598d31265f6a5b2d9baa75c11bd1e05069eb ";
var userId = "rohilshah95";
var urlRoot = "https://api.github.com";
// NCSU Enterprise endpoint:
// https://github.ncsu.edu/api/v3

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

	// Send a http request to url and specify a callback that will be called upon its return.
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

	// Send a http request to url and specify a callback that will be called upon its return.
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

	// Send a http request to url and specify a callback that will be called upon its return.
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

	// Send a http request to url and specify a callback that will be called upon its return.
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

	// Send a http request to url and specify a callback that will be called upon its return.
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

	// Send a http request to url and specify a callback that will be called upon its return.
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

