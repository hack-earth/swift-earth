# swift-earth

A Swift programming assistant. Let's keep this to ourselves for a bit while we see what becomes of it.

## Functionality targets

Roughly in order of implementation:

1. Auto-completion, in a much broader sense than exists today. "Propose some new code at my cursor position."
   One good trick should be writing a comment and then auto-completing it into the code. Another should be 
   writing a function header, putting the cursor inside the brackets, and asking for a function body. Another
   should be typing the names of one or several variables, selecting those, and asking for code that uses them.
   
2. Code suggestions. Given an existing source file (presumably in an editor), suggest improvements.

## General Ideas

### Use GitHub diffs as training data

Given a commit to a public repo on GitHub, we can back out any little piece of the commit to see a hypothetical just-prior state where another change (known to us from the commit) was needed.

Given that just-prior state, think like a programmer. Does it compile? If not, what are the error messages? Read the source.

### [Integrate with the Swift Compiler's Semantic Analysis](https://www.polidea.com/blog/how-to-build-swift-compiler-based-tool-the-step-by-step-guide/)

We will need deep, peculiar integration with the Swift AST and code analysis.

### Use [Swift for Tensorflow](https://www.tensorflow.org/swift) and [swiftai](https://github.com/fastai/swiftai)

Contribute back to those.

## Ideas for Learning

### Code Context

At any given point in the code, we want a deep context. For example, this should include:
* For each identifier in scope:
  * "Meaning" of the name. (When we say "meaning", imagine an embedding.)
  * Type. (Our information about the type should be roughly the same as our information about any identifier in scope.)
  * Scope.
  * How recently the declaration was written (per the Git history) and updated.
* The surrounding scopes, at roughly the same level as for identifiers in scope.
* The immediately preceding code.

One complication for learning is that we want the context in which the code is being written, not the
context in which it already exists. If we are training from GitHub commits, which usually represent a 
relatively finished point in authoring code, then for training we have to back out the code being written.

