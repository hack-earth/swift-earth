# swift-earth

A Swift programming assistant. Let's keep this to ourselves for a bit while we see what becomes of it.

## General Ideas

### Use GitHub diffs as training data

Given a commit to a public repo on GitHub, we can back out any little piece of the commit to see a hypothetical just-prior state where another change (known to us from the commit) was needed.

Given that just-prior state, think like a programmer. Does it compile? If not, what are the error messages? Read the source.

### [Integrate with the Swift Compiler's Semantic Analysis](https://www.polidea.com/blog/how-to-build-swift-compiler-based-tool-the-step-by-step-guide/)

This seems like the state of the art as of this writing.

### Use [Swift for Tensorflow](https://www.tensorflow.org/swift) and [swiftai](https://github.com/fastai/swiftai)

Contribute back to those.

