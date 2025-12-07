# A Gentle Introduction To Statistical Learning Theory

If you’ve taken a machine learning class, one of the first things you learn is to train simple classifier, for this you need to split your data into two sets — a **training set**, where the model learns, and a **test set**, where we see if it actually generalizes.  

So you train your first classifier, maybe it separates cats from dogs, and it reports **98% accuracy** on the test set. That feels incredible. Sure, it makes a few mistakes, but most of the time it’s right.  
Yet here’s the subtle, often-ignored question: **how is this even possible?**  
How can a machine recognize a cat it has never seen before?  

You might say: *“It learns the features of cats from the training data and extrapolates.”*  
But what does it *really* mean to extrapolate?  

That’s not a trivial question, and it doesn’t have an obvious answer.  
In the 1960s, Vladimir Vapnik and Alexey Chervonenkis tried to formalize it.  
Their work gave birth to **Statistical Learning Theory** — or **VC Theory** — which sits at the very foundation of classical machine learning.  

At its core, the theory asks one deceptively simple question:  

> **When does doing well on the training set actually mean we’ll do well on new, unseen data?**

That question reshapes everything we think we know about learning.  

Learning something new almost always feels uncomfortable — that friction isn’t a bug, it’s a feature. Push through it, and you’ll gain tools to reason about learning in a way that borders on magical.  

This series is my attempt to make those ideas intuitive. These are my notes, rewritten the way I wish someone had explained them when I first studied the topic. Together, we’ll wrestle with the deeper question:  

> **What does it really mean to learn?**

---

## Table of Contents
1. [Machine Learning as Automated Inductive Inference](content/01_ml_as_induction)
2. [From Predictions to Risk: Measuring and Approaching Optimal Learning](content/02_risk)
3. [PAC Learnability](content/03_pac_learnability.md)
