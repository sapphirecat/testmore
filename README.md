DANGER
======

API Break
---------

The `testmore.php` script in _this_ repository (sapphirecat/testmore) has **an
API break.**  Skipped tests are handled differently than they are in the
upstream fork.  (I was young and naïve.)

If you **want** the current behavior—which is considered to be
[broken](https://github.com/sapphirecat/testmore/issues/4)—then you should
copy it into your project, and not rely on this one remaining the same, nor
available forever on github.  Skip behavior MAY be changed at any time.


Alternative Package
-------------------

If you’re starting a _new_ set of tests for a project, or just starting a new
project, then you should try [PHPUnit](https://packagist.org/packages/phpunit/phpunit)
instead.  It’s far better supported than this ever will be.


Test::More for PHP
==================

This is a <a href="http://testanything.org/">TAP</a>-compliant PHP testing
library based on <a href="http://search.cpan.org/perldoc?Test::More">Test::More</a>.

Usage
-----

    plan('no_plan');
    # or
    plan(23);
    # or
    plan('skip_all');
    # or
    plan(array('skip_all' => $reason));

    require_ok('my_file.php');
    include_ok('another.php');

    # Various ways to say "ok"
    ok($got == $expected, $test_name);

    is($got, $expected, $test_name);
    isnt($got, $expected, $test_name);

    # Rather than echo "# here's what went wrong\n"
    diag("here's what went wrong");

    like($got, '/expected/', $test_name);
    unlike($got, '/expected/', $test_name);

    cmp_ok($got, '==', $expected, $test_name);

    is_deeply($got_complex_structure, $expected_complex_structure, $test_name);

    skip($why, $how_many);

    can_ok($module, $methods);
    isa_ok($object, $class);

    pass($test_name);
    fail($test_name);

    todo_begin("New frobaz feature");

    ok($got, $expected, $test_name);
    # ...

    todo_end();

    # Or under 5.3
    todo( "New frobaz feature", function () {
        ok( $got, $expected, $test_name );
        # ...
    });

Testing the tests
-----------------

If you have Perl's <a href="http://search.cpan.org/dist/Test-Harness/">Test::Harness</a> installed (you almost certainly do), you can run the tests using:

    prove --exec 'php' test/test.php

Credits
-------

Originally inspired by work from Andy Lester. Written and  maintained by Chris Shiflett.

For contact information, see: http://shiflett.org/contact 
