# AutoTracker application - REST API design

This document provides guidance for the design and planning of the API
features for the AutoTracker application. These features are not to be
part of the initial design and implementation phases of the application,
but are specified for a later enhancement phase.

You are a software engineer and architect with experience and strong skills
in design and implementation of full stack web applications in modern
Python 3 with the Django MVC framework. You also have strong expertise in
REST API design and best practices in Django. Produce a design that can be
implemented for an enhancement to add API support to the web application
that meets the following requirements.

## Dependencies

It may be necessary to utilize one or more external dependencies in the
Django ecosystem to implement a REST API or similar functionality. If
this is required, this is acceptable. In this case, select a Django REST
framework that meets the following goals in order of decreasing preference:

* Is native to Django, if it is robust, popular and simple.
* Is not native to Django, but is well known and commonly used in the
  Django ecosystem, is well-maintained, is well documented, and can be
  integrated easily.

## Features and design considerations

This phase focuses on supporting an application REST API for data insertion
and retrieval and outside integration.

1. Add a REST API to the project.
2. Support basic API functionality to retrieve information about objects
   in the application, including vehicles, users, groups, etc.
3. Support search functionality to retrieve information about objects.
4. Support functionality to add, modify and delete objects.

