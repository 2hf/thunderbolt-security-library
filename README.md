# thunderbolt-security-library
An advanced and multiuse security library for C++ (C++17 and above) in the works.

* Main.cpp example:
   ```cpp
  	thunderbolt::start_thunderbolt( );
	thunderbolt::c_function thunderbolt_initialize_function( thunderbolt::initialize_library, thunderbolt::initialize_library_stub );
	thunderbolt::c_entropy thunderbolt_initialize_entropy;
	thunderbolt_initialize_entropy.add_element( thunderbolt_initialize_function );
	if ( thunderbolt::initialize_library( ) ) {
		thunderbolt_initialize_entropy.erase_functions( );
		thunderbolt::start_threat_detection_threads( );
		thunderbolt::handle_threat_detection_threads( ); 	
		{
		    // do program stuff
		} thunderbolt::end_threat_detection_threads( );
	}
	else {
		thunderbolt_initialize_entropy.erase_functions( );
		thunderbolt::end_thunderbolt( );
		ExitProcess( EXIT_FAILURE );
		return EXIT_FAILURE;
	}

	thunderbolt::end_thunderbolt( );
   ```
   
 * Main functions
```
start_thunderbolt - prepares library
initialize_library - initializes library, startup integrity and security checks
start_threat_detection_threads - pushes security threads (optionally custom threads) to thread deque
handle_threat_detection_threads - handles these threads
end_threat_detection_threads - shuts down threads
end_thunderbolt - ends thunderbolt security library
```

 * Classes
```
c_function -  stores size and ptr to function
c_entropy - allows for erasing of function instructions on runtime, useful for one-time functions that are important
c_obfuscation - obfuscating code on runtime as well as compiletime
c_junk - junker class, injects junk code and handles artifacts properly
```
