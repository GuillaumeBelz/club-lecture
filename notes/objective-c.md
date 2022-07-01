
# Objective-C

## Sources

- https://www.tutorialspoint.com/objective_c/index.htm
- https://www.tutorialspoint.com/ios/index.htm

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

```
/* function returning the max between two numbers */
- (int) max:(int) num1 secondNumber:(int) num2 {
   
   /* local variable declaration */
   int result;
 
   if (num1 > num2) {
      result = num1;
   } else {
      result = num2;
   }
 
   return result; 
}
```

```
@interface SampleClass:NSObject
/* method declaration */
- (int)max:(int)num1 andNum2:(int)num2;
@end

SampleClass *sampleClass = [[SampleClass alloc]init];
ret = [sampleClass max:a andNum2:b];
```

## Blocks

```
returntype (^blockName)(argumentType);

returntype (^blockName)(argumentType)= ^{
};
```

```
void (^simpleBlock)(void) = ^{
   NSLog(@"This is a block");
};

simpleBlock();
```

```
double (^multiplyTwoValues)(double, double) = 
   ^(double firstValue, double secondValue) {
      return firstValue * secondValue;
   };

double result = multiplyTwoValues(2,4); 
NSLog(@"The result is %f", result);
```

```
#import <Foundation/Foundation.h>

typedef void (^CompletionBlock)();
@interface SampleClass:NSObject
- (void)performActionWithCompletion:(CompletionBlock)completionBlock;
@end

@implementation SampleClass

- (void)performActionWithCompletion:(CompletionBlock)completionBlock {

   NSLog(@"Action Performed");
   completionBlock();
}

@end

int main() {
   
   /* my first program in Objective-C */
   SampleClass *sampleClass = [[SampleClass alloc]init];
   [sampleClass performActionWithCompletion:^{
      NSLog(@"Completion is called to intimate action is performed.");
   }];

   return 0;
}
```

Méthodes de `NSNumber` :

```
(NSNumber *)numberWithBool:(BOOL)value
(NSNumber *)numberWithChar:(char)value
(NSNumber *)numberWithDouble:(double)value
(NSNumber *)numberWithFloat:(float)value
(NSNumber *)numberWithInt:(int)value
(NSNumber *)numberWithInteger:(NSInteger)value

(BOOL)boolValue
(char)charValue
(double)doubleValue
(float)floatValue
(NSInteger)integerValue
(int)intValue
(NSString *)stringValue
```

## Strings

`NSString` et `NSMutableString`

```
#import <Foundation/Foundation.h>

int main () {
   NSString *greeting = @"Hello";
   NSLog(@"Greeting message: %@\n", greeting );

   return 0;
}
```

```
(NSString *)capitalizedString;
(unichar)characterAtIndex:(NSUInteger)index;
(double)doubleValue;
(float)floatValue;
(BOOL)hasPrefix:(NSString *)aString;
(BOOL)hasSuffix:(NSString *)aString;
(id)initWithFormat:(NSString *)format ...;
(NSInteger)integerValue;
(BOOL)isEqualToString:(NSString *)aString;
(NSUInteger)length;
(NSString *)lowercaseString;
(NSRange)rangeOfString:(NSString *)aString;
(NSString *)stringByAppendingFormat:(NSString *)format ...;
(NSString *)stringByTrimmingCharactersInSet:(NSCharacterSet *)set;
(NSString *)substringFromIndex:(NSUInteger)anIndex;
```

## Structures 

```
struct [structure tag] {
   member definition;
   member definition;
   ...
   member definition;
} [one or more structure variables]; 
```

## Classes & Objects

```
@interface Box:NSObject {
   //Instance variables
   double length;    // Length of a box
   double breadth;   // Breadth of a box
}
@property(nonatomic, readwrite) double height;  // Property

@end

Box box1 = [[Box alloc]init];     // Create box1 object of type Box
Box box2 = [[Box alloc]init];     // Create box2 object of type Box

```

