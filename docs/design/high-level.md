# AutoTracker application - overall design

This document provides the top level starting point for the design and planning of the AutoTracker application.

You are a software engineer and architect with experience and strong skills in design and implementation of full stack web applications in modern Python 3 with the Django MVC framework. Produce a design that can be implemented for a web application that meets the following requirements.

## General information and purpose

* Application name: AutoTracker
* Application purpose: automobile information and maintenance tracking and management
* Application complexity: aim for an architecture and design that is relatively simple and eschews complexity so that intermediate level Python developers and users may be able to understand it, install it, document it, enhance and extend it, and troubleshoot it without dealing with significant complications.

## Dependencies

Application dependencies: try to keep dependencies to a minimum.

* Django is an obvious dependency, and provides a lot of functionality that can be utilized out of the box. Prefer the use of standard functionality and framework included in Django unless there is a strongly compelling reason or hard requirement that necessitates the use of an external dependency.

Application software stack:

* Python 3. The application should work on all supported releases of Python 3 from 3.10 onward, but don't worry about prelease or development versions. 
* Django web framework (should operate properly on all currently supported releases of Django).
* Database:
    * Database type: Support traditional RDBMS, with PostgreSQL preferred for production and SQLite3 for development.
    * ORM: Use the native Django ORM.
    * Migrations: Use migrations as it is likely that future enhancements will lead to schema changes.

Package deployment:
* If installing software, install into a Python virtual environment and do not modify or pollute the system Python environment. All Python invocations should come from this virtual environment.

Testing and code quality:
* Use `pytest` for the test framework.
* Ensure unit tests and basic integration tests.
* Use `tox` for automation and orchestration of the test framework and to invoke linter(s), formatter(s), etc.
* Use `black` for automatic Python code formatting.
* Ensure Python code conforms to PEP 8.

## Packaging

* Packaging: the application should be able to be packaged using modern Python packaging practices, use a pyproject.toml file for managing dependencies and builds, etc.
* Containerization: optional and planned as a deployment enhancement in a future phase.

### Features and design considerations

The core features and elements of the application are as follows:

* The application is multi-user.
* All users will be created by administrators. User will not sign up or register in this application. User email addresses are considered to be valid because they've been entered by an administrator or set by a user.
* A default administrator is created on first use. This administrator user can be used to create and manage other users. The default administrator's email should be `admin@autotracker.local` and a unique, 15 character alphanumeric password should be generated for this default admin account. The user should be encouraged to change the password and update the email address after first logging in with this user.
* The application allows users to input, provide detail, and track information related to automobiles they own and/or operate. For vehicles, this information should include: vehicle information and attributes like make, model, color, style/trim, year, VIN, condition, milage at time of purchase, current mileage, tire specs, engine specs, transmission type, vehicle internet URL, MSRP, purchase price, KBB value, oil type, brake fluid type, and other important details about an automobile related to operating and maintaining it properly.
* User profiles should support name and email address.
* Objects/models should all include standard tracking and audit metadata:
    * Created date
    * Last modified date
    * Created by user
    * Last modified by user

#### Frontend considerations

* Frontend considerations and user experience: HTML5, CSS, JavaScript, images; the application may use a frontend framework, however it should not implement significant business logic in a heavy frontend framework.
* Most business logic to be done in Python and less should be done in JavaScript.
* Object deletion should be confirmed by the user. 
* For CSS/components, etc., use Tailwind and a leading, supported, maintained library or plugin for Tailwind.
* Icons should be used throughout, but they should be fairly simple, monotone, tasteful, modern, elegant, and not overused.
* Use a clean, semantic URL structure and ensure that the design enables the application to have explicit URLs for all objects (and avoid a design that is very heavily JavaScript based that would make it difficult to navigate or hyperlink to specific objects or views, etc.). Avoid the use of very heavy parameter-based URLs where possible.
* Styling for the site should be done with the use of themes.
    * All styling for the application, including color schemes, icons, etc. is configured in a theme.
    * Favor a dark mode experience in the UI and in several theme designs.
    * A default theme is present in the application, configured as a default for new deployments. 
    * A default themes may be specified by an administrator in the Django settings.
    * A theme may be selected by users (so that a user may select a preferred theme for their profile). This selection may override the default specified by the administrator, if it is set in the user's profile.
    * Produce a set of five bundled themes for the application that are based on excellent color palettes or color schemes.
    * Use styles and color schemes that work with an automotive, car, truck or related topics.
    * The default theme should be clean and subtle with use of blues and grays included in the pallete.

#### Object types

The application should support the following types of objects:

* Users: these are application users that log in to the application and use it, including administrators and non-administrative users.
* Groups: these are groups of application users that can be used for access control and notifications.
* Vehicles: these are vehicles such as cars, trucks, SUVs, motorcycles, boats, RVs, ATVs, etc.
* Suppliers: these are parts suppliers, dealerships, or mechanic shops.  Attributes of suppliers should include a type, phone number, email address, street address, and website. 

## Security considerations

Refer to `@docs/design/security.md` for considerations related to application security design and features. Integrate this into overall application design and across phases of design and implementation as needed.

## Functional requirements

Vehicle management:

1. Support CRUD operations for vehicles and suppliers. Users can list, search for, add, remove and modify vehicles and suppliers, including numerous attributes for each vehicle.

User and group management:

1. Support CRUD operations for user objects and group objects.
2. Administrators can manage users and groups, including adding them, modifying them, deleting them, and enabling or disabling them. Admins can also manage RBAC and roles within the application.
3. Users (non-administrator users) can manage and modify their own user profiles, can change their own passwords, but cannot otherwise modify their accounts or other users' accounts or groups in other ways.

## Roadmap

### Phase 1 - Core application design

This phase focuses on core application setup with focus on these elements:

1. Creating the basic framework and architecture for the application.
2. Simple, single-factor password based authentication.
3. Focus on fundamental application security, ensuring that common and relevant web application security risks, database security risks, and authentication and credential security risks are considered and enabled in Django. Details on this are provided in `@docs/design/security.md`.
4. Core functional requirements are met in this phase:
    * Support for vehicle management (CRUD operations).
    * Support for user management (CRUD operations).
    * Support for group management (CRUD operations).
    * Support for supplier management (CRUD operations).
5. Functional, elegant web UI with a default theme.

### Phase 2 - Maintenance tracking support

This phase focuses on adding in support for tracking maintenance information and history for vehicles.

1. Add maintenance features to the application as described in `@docs/design/feature-support-maintenance.md`.

### Phase 3 - Authentication security

This phase focuses on enhancing authentication security in the application to give users options for MFA.

1. Add support for MFA as described in `@docs/design/security.md`.

### Phase 4 - Containerization support

This phase focuses on supporting containerization as a deployment option for the application.

Guidelines: container deployment should be an optional convenience for the user, and is not the default or the only deployment option.

1. Add maintenance features to the application as described in `@docs/design/deployment-support-containerization.md`.

### Phase 5 - API support

This phase focuses on supporting an application REST API for data insertion and retrieval and outside integration.

1. Add maintenance features to the application as described in `@docs/design/feature-support-api.md`.

