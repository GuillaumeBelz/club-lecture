
# Objective-C

## Sources

- https://openclassrooms.com/fr/courses/149791-programmez-en-objective-c
- https://openclassrooms.com/fr/courses/4206426-introduction-a-ios-plongez-dans-le-developpement-mobile
- https://www.tutorialspoint.com/objective_c/index.htm

## Hello World

```
#import <Foundation/Foundation.h>

int main (int argc, const char * argv[]) {
   NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
   
   NSLog (@"hello world");
   [pool drain];
   return 0;
}
```

## Program Structure

```
#import <Foundation/Foundation.h>

@interface SampleClass:NSObject
- (void)sampleMethod;
@end

@implementation SampleClass
- (void)sampleMethod {
   NSLog(@"Hello, World! \n");
}
@end

int main() {
   SampleClass *sampleClass = [[SampleClass alloc]init];
   [sampleClass sampleMethod];
   return 0;
}
```

## Functions

```
- (return_type) method_name:( argumentType1 )argumentName1 
joiningArgument2:( argumentType2 )argumentName2 ... 
joiningArgumentn:( argumentTypen )argumentNamen {
   body of the function
}
```


