# HW1

Name : Rohil Shah  
Unity ID: rshah8  
Student ID: 200204305


Link to gh-pages website: [https://pages.github.ncsu.edu/rshah8/HW1/](https://pages.github.ncsu.edu/rshah8/HW1/)

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

Code for REST tasks: [https://github.ncsu.edu/rshah8/HW1/blob/master/script.js](https://github.ncsu.edu/rshah8/HW1/blob/master/script.js)

