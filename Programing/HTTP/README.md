# [ HTTP ]

## [ API ]

### [ REST ]

  References:
    http://restful-api-design.readthedocs.org
    https://github.com/interagent/http-api-design
    http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html
    http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api

#### [ Collection ]

  Resources can be grouped into collections. Each collection is homogeneous so that it contains only one type of resource, and unordered.

  Example:

  /api/:coll	    A top-level collection named “coll”
  /api/:coll/:id	The resource “id” inside collection “coll”

  References:
    http://restful-api-design.readthedocs.org/en/latest/resources.html#resources

#### [ Resource ]

  A resource is an object with a type, associated data, relationships to other resources, and a set of methods that operate on it. It is similar to an object instance in an object-oriented programming language, with the important difference that only a few standard methods are defined for the resource (corresponding to the standard HTTP GET, POST, PUT and DELETE methods), while an object instance typically has many methods.

  References:
    http://restful-api-design.readthedocs.org/en/latest/resources.html

#### [ CORS ]

  References:
    https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS
    http://www.jongleberry.com/understanding-csrf.html
