Main Entry Point (main.dart)
============================

The **main.dart** file is the starting point of the Flutter application. It contains the minimal logic needed to bootstrap the app, delegating all configuration to dedicated *core* modules.

Overview
--------

The ``main()`` function calls ``runApp`` with a ``const CookApp()`` instance. The ``CookApp`` class is a ``StatelessWidget`` that builds the ``MaterialApp`` with:

- A custom light theme from ``AppTheme.lightTheme``.
- The initial route set to the login page via ``AppRoutes.login``.
- A centralized route generator ``AppRoutes.generateRoute`` to handle all named routes dynamically.

This design keeps the entry point clean. All theme and routing definitions live in separate files under `core/`, effectively acting as configuration namespaces.

Widget: CookApp
---------------

**Type:** ``StatelessWidget``

**Properties:**

- ``title`` – "Cook App", displayed in the task switcher and other OS integration points.
- ``theme`` – Reference to ``AppTheme.lightTheme`` (defined in ``core/theme.dart``).
- ``initialRoute`` – ``AppRoutes.login`` (defined in ``core/routes.dart``), the first screen shown after launch.
- ``onGenerateRoute`` – ``AppRoutes.generateRoute``, a function that returns a ``Route`` based on the route name and arguments, enabling scalable navigation without hardcoding routes in ``MaterialApp``.

Code
----

.. code-block:: dart

    import 'package:flutter/material.dart';
    import 'package:frontend/core/routes.dart';
    import 'package:frontend/core/theme.dart';


    void main(){
        runApp(const CookApp());
    }

    class CookApp extends StatelessWidget {
        const CookApp({super.key});
    // basically redid main and moved everything out 
    // all core files are basically just name spaces 
        @override
          Widget build(BuildContext context) {
            return MaterialApp(
                title: "Cook App",
                theme: AppTheme.lightTheme, 
                initialRoute: AppRoutes.login,
                onGenerateRoute: AppRoutes.generateRoute
            );
          }
    }
