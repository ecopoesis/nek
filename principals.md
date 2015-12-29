Here's a list of goals for nek:

* no nulls
* final/sealed by default
* prefer immutable variables
* option types: Foo?
* no exceptions: error types that extend option types (all errors are options). this is like Scala's Try: Foo#
* thread instead of def? automatic threadpools?
* def vs var?
* no = just := for assignment and == for comparison

FizzBuzz
------------
    def fizzBuzz(items: Integer) := {
        (1..items).foreach (i) -> {
            if (i % 3 == 0 && i % 5 == 0) {
                print('fizzbuzz\n');
            } elsif (i % 3 == 0) {
                print('fizz\n');        
            } elsif (i % 5 == 0) {
                print('buzz\n');
            } else {
                print(i + '\n');
            }          
        }
    }
