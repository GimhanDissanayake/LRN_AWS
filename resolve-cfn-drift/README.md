# Resolve drift with an import operation

URL: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/resource-import-resolve-drift.html

## Steps
1. Create cfn stack
2. User changed a resource outside of CloudFormation
3. Detect drift
4. Add a DeletionPolicy attribute, set to Retain, to the resource 
  - This ensures the existing resource is retained rather than deleted when it's removed from the stack.
5. Remove the resource from the template and run a stack update operation
  - This removes the resource from the stack, but doesn't delete it.
6. then import the existing resource back into the stack
  - This adds the resource back into the stack and resolves the property differences that were causing the drift results

## Resolving drift for a resource through an import operation consists of the following basic steps:

Add a DeletionPolicy attribute, set to Retain, to the resource. This ensures the existing resource is retained rather than deleted when it's removed from the stack.

Remove the resource from the template and run a stack update operation. This removes the resource from the stack, but doesn't delete it.

Describe the resource’s actual state in the stack template, and then import the existing resource back into the stack. This adds the resource back into the stack and resolves the property differences that were causing the drift results.

