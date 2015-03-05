#JS-RS (A Work In Progress)

This is an experimental Rest Service for JavaScript leveraging AtScript and TypeScript. This code is highly influenced by
the new Angular2.0 being developed and the JAX-RS spec from the land of Java.

### Example of a resource class
a complete example can be found in JS-RS/test/test-resource.ats

```javascript

@Path('/example-resource')
export class ExampleResource extends Resource {

    @GET
    @ReturnsArray(TestModel)
    @Path('/example')
    queryExampleResource(@QueryParam('sort') sortDirection) {}

    @GET
    @ReturnsObject(TestModel)
    @Path('/example/{id}')
    getExampleResource(@PathParam('id') id:number) {}

    @POST
    @ReturnsObject(TestModel)
    @Path('/example')
    postExampleResource(@RequestBody testModel) {}

    @PUT
    @ReturnsObject(TestModel)
    @Path('/example/{id}')
    putExampleResource() {}

}
```

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
