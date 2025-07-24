# ai-rulesets

WIP - Rules for code generation. Primary use is currently unit test generation.

-------
```
1. When working on Angular apps do the following "general rules"
   1. Follow all linting and prettier configuration and autofix any issues
   2. Remove any unused variables
   3. Avoid usage the "any" type or "as any"
   4. Use standalone components, directives, and pipes instead of NgModules
   5. Implement control flow with @if, @for, and @switch instead of *ngIf, *ngFor, etc.
   6. Leverage functional guards and resolvers instead of class-based ones
   7. When adding CSS classes use tailwind
   8. Prefix all tailwind classes with "tw-" otherwise they won't work
   9. Build UI layouts with responsive design in mind
   10. Add "data-testid" attribute to actionable components like buttons and anchor tags
2. When making a unit test for Angular apps do the following "unit test rules"
   1. Use the Angular "general rules" for tests
   2. Utilize ngMocks https://ng-mocks.sudo.eu/ for effective dependency mocking within tests
   3. Use jest with typescript
   4. Dont use TestBed instead use ngMocks "MockBuilder" with builder syntax like .mock(), .keep(), .provide()
   5. Put a ngMocks "MockRender" function in each "it()" block
   6. Dont put "MockRender" into "beforeEach()"
   7. Use ngMocks "ngMocks.find()" to find elements in the template, always find them by "data-testid" attribute
   8. Use "provideMockStore" from "@ngrx/store/testing" to mock out selectors
   9. Name the top level "describe" with space separated words, for example "My Data Service"
   10. Never use jasmine
   11. Allow typescript types to be inferred vs explicitly defined
   12. Leverage https://ng-mocks.sudo.eu/extra/customize-mocks to place mocks at the correct scope
   13. When a test needs to test HTTP be sure to put in "provideHttpClient" and "provideHttpClientTesting"
   14. When a test needs to test HTTP be sure to put httpMock.verify() at the very end of the test
   15. When a test needs to test HTTP be sure to .keep(BaseService) since ngMocks will automock
   16. When testing components, always interact with the DOM / HTML using data-testid attributes over calling functions directly from a component instance.
   17. When using "MockInstance" be sure to put "MockInstance.scope()" at the top of the test file
   18. Don't make a function that calls MockRender that is resuable, duplicate MockRender calls
   19. ngMocks is setup to automock so don't add .mock() unless it puts adds a mock / stub
   20. Follow and structure tests using Arrange, Act, Assert format
   21. Avoid writing tests that perform actions but don't assert anything
   22. Aim to test the important parts of the code, having high coverage isn't the top priority
   23. Don't mix jests "done()" with "async" in a test. Jest warns it can be bad practice.
   24. Keep the setup in "beforeEach" minimal, ideally it would just be ngMocks "MockBuilder"
```
