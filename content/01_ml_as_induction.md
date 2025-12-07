# Machine Learning as Inductive Inference

Machine learning can be thought of as **automated inductive inference**. To unpack that, let’s step back and recall two classic modes of reasoning: **deduction** and **induction**.

**Deductive inference** means reasoning from the general to the specific.  
Example: *All cats are mammals. Whiskers is a cat. Therefore, Whiskers is a mammal.*  

If the premises are true, the conclusion must be true. The challenge is usually not the logic itself but the uncertainty in whether the premises are correct.

**Inductive inference** flips this around. Here we reason from specific cases to broader generalizations.  
Example: *Whiskers is a cat, Whiskers is a mammal. Fluffy is a cat, Fluffy is a mammal. Maybe all cats are mammals?*  

Notice the key difference: even if every observed case is correct, the leap to a global statement is uncertain. That uncertainty is built into induction itself.

Machine learning sits firmly in the inductive camp. At its core, it’s about **automating the leap from particular examples to general rules**.  

For concreteness, the rest of our analysis will focus on **supervised learning**, where the data comes in the form of paired inputs and outputs.

---

## A Philosophical Framing

We want to understand nature, and this can mean two things:

There is **nature**, some unknown process that generates the raw events we encounter. Then there are **objects** that take an event and produce a consequence. When we put the two together — the event and the consequence — we get what we’ll call an **observation**.  

All we really have is a **collection of observations**. We don’t know how nature produces the events. We don’t know the rule the object follows to generate consequences.  

**Given a number of observations, can we discover a rule that captures the behaviour of the object?**

But the real challenge is not only to explain the past. We want to predict how the object will respond to **new events** it has never seen.  

As stated, the problem is underspecified. For instance:  
* What if nature always produces the same event?  
* What if the object outputs consequences at random, with no regularity?  

Without further structure, the task of learning is meaningless. To make it well-posed, we need to assume at least:  

1. **Consistency:** Events and consequences must be connected in some way. If outcomes are just random noise, there’s nothing to learn.  
2. **Independence:** Observations should come from similar conditions and not directly influence each other. Otherwise, each new observation wouldn’t really teach us anything new (this is what the independent and identically distributed, “i.i.d.” assumption captures).  
3. **Rule space:** We need to have some idea of what kind of rules the object might be using. If every possible rule is allowed, learning is impossible. (We will return to this later when we discuss the **no-free lunch theorem**.)

With these assumptions in place, the supervised learning problem becomes well-defined.

From here on, we’ll start introducing mathematical notation. The goal isn’t to make things harder, but to make things precise. The philosophical framing gave us intuition, but mathematics gives us the exact language we need to define and reason about learning.

I’ll always describe the ideas in plain language first, then show how they look in symbols. If you see a symbol you don’t recognize, don’t just skip over it — pause, look it up, read it out loud, try to connect it back to the words. That’s how you get comfortable with the notation.

And don’t stop here: explore other explanations, check different textbooks, watch videos, play around with examples. The more angles you see an idea from, the deeper it will stick.

This is where the real fun begins.

---

## A Mathematical Formulation

![fundamental_ml_problem_setting_diagram](fundamental_ml_problem_setting_diagram)  

We are given **independent and identically distributed (i.i.d.) observations**  

$$(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n),$$  

where each input \(x\) belongs to the set of all possible inputs (**input space** \(\mathcal{X}\)),  
and each output \(y\) belongs to the set of all possible outputs (**output space** \(\mathcal{Y}\)).  

These pairs are assumed to come from a fixed but unknown **joint probability distribution**  

$$P(x, y) \quad \text{over } \mathcal{Z} = \mathcal{X} \times \mathcal{Y}.$$  

This distribution can be factorized as  

$$P(x, y) = P(x)\, P(y \mid x),$$  

which highlights two complementary sources of uncertainty:  

1. **Input generation**: the marginal distribution \(P(x)\), describing how nature produces inputs.  
2. **Output generation**: the conditional distribution \(P(y \mid x)\), describing how an object maps inputs to outputs — possibly in a non-deterministic way.  

The goal of supervised learning is to build a **predictor function**  

$$f : \mathcal{X} \to \mathcal{Y}$$  

that models the relationship between inputs and outputs as faithfully as possible to the true distribution \((X, Y) \sim P\).  

But what does “faithfully” or “better” actually mean?  
In the [next lesson](02_risk), we’ll tackle how to measure predictive quality.
