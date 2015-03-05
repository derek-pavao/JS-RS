#JS-RS (A Work In Progress)

This is an experimental Rest Service for JavaScript leveraging AtScript and TypeScript. This code is highly influenced by
the new Angular2.0 being developed and the JAX-RS spec from the land of Java.

###An Example:

You have a REST Service that performs CRUD on a Person model say. There are endpoints like GET /person that gets a list of people, GET/person/{person_id} that gets one Person, POST /person that takes a Person model in the body of the request and creates a new Person model, and PUT /person/{person_id}

You might use something like JS-RS to write a client to interact with your rest service. That client might look like the following

```javascript
@Path('/person')
class PersonResource extends Resource {
    
    @GET
    getPersonList() {}

    @GET
    @Path('/{person_id}')
    getOnePerson(@PathParam('person_id') personId) {}


    @PUT
    @Path('/{person_id}')
    updatePerson(@PathParam('person_id') personId, @RequestBody personModel) {}

    @POST
    createPerson(@RequestBody personModel) {}

}
```

Two things to note here:
 - The lack of method bodies, they are actually not necessary
 - Each of these methods will return a Promise

Now that you have a PersonResource class you can use it to make requests to the server to get people, something like


```javascript

var personResource = new PersonResource();

/**
 * Retrieving a list of people
 */
personResource.getPersonList().then(function (personList) {
    // do something with personList
});


/**
 * and creating a new person
 */
var personModel = {
    firstName: "Joe",
    lastName: "Jackson"
};

personResource.createPerson(personModel).then(function () {
    // the person is done being created
});
```

So using JS-RS you could create an object to interact with your backend service, without actually writing any code. Most of these ideas come from the JAX-RS spec, a spec in Java for creating and interacting with REST services.


### Initial setup
```bash
# Clone the repo...
git clone https://github.com/dotDeeka/JS-RS.git
cd JS-RS;

# Then, you need to install all the dependencies...
npm install

# If you want to be able to use global commands `karma` and `gulp`...
npm install -g karma-cli gulp
```

### Running the tests
The tests are in `JS-RS/test/resource_spec.ats`. Run them using Karma, like so:
```bash
karma start
```
Karma opens a browser window for running tests. To see the actual test output (and errors), look for the log in the terminal window where you issued the `karma start` command.

###Thanks to these projects:

[AtScriptPlayground - https://github.com/angular/atscript-playground](https://github.com/angular/atscript-playground)

[AtScript - http://atscript.org](http://atscript.org)

[Traceur - https://github.com/google/traceur-compiler](https://github.com/google/traceur-compiler)

[RequireJS - http://requirejs.org](http://requirejs.org)

[Assert - https://github.com/angular/assert](https://github.com/angular/assert)

[Karma - http://karma-runner.github.io/](http://karma-runner.github.io/)

[Gulp - http://gulpjs.com](http://gulpjs.com)
