Code is decent. It uses dependency injection.

First of all, this is the wrong implementation of the Repository Pattern. What you need to do here first is to create an interface and use inversion of control to use that repository. So for example, you have a BaseRepositoryInterface and a BookingRepositoryInterface. The purpose of the Repository pattern is so that you can interchange the type of database access. For example, you have a MySQL repository, MongoDB Repostiory, EloquentRepository, etc... Anyway, it is best to create a Service class here instead. I won't refactor this but in the controller it should be BookRepostioryInterface and the isntance will be an instance of EloquentBookRepository.

spacing is not my cup of tea but i will not refactor it because it's the code standards of the team.
the request->__authenticatedUser is bad. unfortunately, i cannot refactor it but mostly properties with _ means it's a private property. It's better to use a getter like $request->getUser()

I won't refactor Booking Repository anymore cause it's horrible. A lot of nested conditions. Spacing problems. Unclear variables. You get what I mean. One more thing. Don't use Mailer inside the repository. The repository's job is only to handle database calls.

Here are the things I will refactor:

* using env directly in code is bad also, what you gonna do here is use a global config method or inject a config dependency cause it's global.
* Also response variables need to be clear. Like, what are we getting here for the response? Is it a job or is it users?
* You can use ternary conditions to shorten 2 if statements.
* So far, you use JSON respone. It's better to follow a specific structure for JSON responses these days. The best I can think of is to put the response in data.
* distanceFeed method is rather long and you need to create a service class to handle those things. If this was a Laravel project, you can use depedency injection in the method.
* Also you can use the message property in the response to give out messages.
* Spacing on variable declarations and method calls is crucial.
