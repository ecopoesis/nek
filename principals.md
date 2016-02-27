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


Let's think about blocks/lambda/functions:

function:

    def funcName(arg1: Type, arg2: AnotherType) := {
        ...
    }
    
function no args:

    def funcNoArgs := {
        ...
    }
    
type:
    
    Integer
    
generic type:
    
    List<Integer>
    
parameterized type:

    Integer[min = 0, max = 255]
    
generic + parameterized type:    

    List<Integer[min = 0, max = 255]>[minLength = 2, maxLength = 2]
    
type alias:

    MyList alias List<Integer[min = 0, max = 255]>[minLength = 2, maxLength = 2]
    
Type aliases are just an alias. If a function takes an alias as a param, it really takes whatever the alias resolves to.
The compiler resolves the aliases down and then drops them.

function type:
    
    Function[params: List<Type>]
    
Function is a special type. All functions inherently descend from it. It's used for functions that normally take lambdas. For example, List.map is declared as:
     
    class List<T> {
        abstract map(Function[params = ??? list literal of one item of type T ???]) 
    }
    
Literals ???:

    list(1, 2, 3)
    map(a -> 1, b -> 2, c -> 3)
    
Reserved words:
* abstract
* class
* def    