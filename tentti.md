# Tentti 18.12.

## 1

### a.
GOFAI means a paradigm of AIs most prevalent in the 1980s. The counterpart to which is
the later emerged "modern AI".

### b.

GOFAI is best defined by being based on logic and rules. It manipulates different "symbols"
and reaches the answer through it. Becuase the real world doesn't always follow strict 
rules and as such the GOFAI's biggest weakness is it's inability to handle uncertainty
and imprecise information. The plus is that it doesn't require huge training sets
compared to the ones used by ML approaches. In general ML approaches are more versitile
than GOFAIs but more expensive to "set up". ML approaches utilize possibly huge amounts
of data and recognizes patterns in it and generates a general model.

ML approaches are also a lot closer to "black boxes" from which the solution "just appears"
compared to GOFAIs.

### c.
GOFAI is best used to solve clearly defined and isolated problems. If the problem
is well-defined with precise data and a clear solution, it's the GOFAIs job.

### d.
One example of a classic GOFAI system is a chess engine. It often utilizes alpha-beta
pruned min-max algorithm with other modifications and additions to make it "smarter".

### e.
People had high hopes for GOFAI to be able to translate and/or understand speech but
these hopes were in vain. This lead to spending being cut which let people even more
dissapointed -> AI winter.

### f.
The philosophy of AI is mostly concerned with determening whether a machine can be
"intelligent".

### g.
Turing had come up with the Turing test that says that if you cannot dedouce AI answer
from a human answer from an interraction with written messages, the AI is said to have 
reached "human-level intelligence". The Turing's view highlighted that if the AI answer
is indistinguishable from the human answer, the AI must have understood what it was
doing and must be "intelligent".

The opposite of this was the view of Searle who had invented the Chinese room -thought 
experiment. In the thought experiment a non-chinese speaking person is sealed in a box 
and is given messages in chinese from outside. The person in the box has a big manual 
from which he can find an answer to all questions. If now a person outside the box
gives the box a message in chinese, it answers back in chinese. The person outside would
get the impression that he is having a conversation with a chinese-speaking person
which is not the case. This opposes Turing's test which says that the output determines
the intelligence of the "AI".

# h.

## 2

### a.
We want to solve P(spam | "free", "offer").
By Naive Bayes clasifier we can write the probability as:
P(spam | "free", "offer") = P(spam)*P("free", "offer" | spam) / P("free", "offer")
and avoiding the denominator:
R = P(spam)*P("free", "offer" | spam) / P("free", "offer") =
R = P(spam)*P("free", "offer" | spam) / P(ham)*P("free", "offer" | ham) =
R = (P(spam) * P("free" | spam) * P("offer" | spam)) / (P(ham) * P("free" | ham) * P("offer" | ham)) =
R = (0.4     * 0.7              * 0.8)               / (0.6    * 0.2             * 0.3)
R = 6.2222...

Then at last we get the probability from R / (1 + R) = 0.216216... ≈ 21.6%

### b.
It assumes that P(X_1, X_2, ... X_n | state) = P(X_1 | state) * P(X_2 | state) * ... * P(X_n | state).
Single (X_i | state) are easy to estimate from training data but estimating the
probability of all the permutations of the words would require vastly more data. 

### c.
K-Nearest Neighbors is a simple learning algorithm that (assuming the data is two-
dimensional coordinates (x,y)) collects the training data and then compares the test
input to the training data. It chooses the k closest items from the training data to the
test input and determines the result by the classes of the matched neighbors.

The choosing of k is of course important because too small of a k and your test results
can vary wildly because a few, for example, items of class "blue" in a sea of "orange"
would return "blue". Also too big of a k and then the model will not pick up on
small enough patterns and will be inprecise.

### d.
Perceptron is a single-layer NN. It consists of a single neuron, the perceptron that
classifies linearly separable problems. The perceptron classifies the binary sets
by "drawing a line" through the origin and checking if all of the points are correctly
classifiend and adjusting the weights if they are not. In the case of non-linearly 
separatable data-sets the perceptron would just keep updating the weights because it 
cannot find a proper line.

### e. 
Linear regression jumps from 0 to 1 in an instant where the logistic regression 
smoothly transfers from 0 to 1. 

## 3

### a.
A transformer contains a tokenizer that transforms the input text tokens which
are easier to handle by an algorithm. Next the tokens are sent into the embedding layer
which combines the tokens with the position of the token in the data and transforms the
data into vectors. After that the data is put into the transformation layers which transform 
the data multiple times, decoding and encoding the data to extract increasing amounts of 
information about the text. After all this the data is then de-embedded and gives back a 
probability distribution of the tokens.

### b. 
Transition from RNN to CNN happened, not because CNN was that superior to RNN, but because
it was more scalable and parallizable. RNN struggled to scale to bigger training sets and
was slower to train which made CNN the better option.

### c.
This approach of fine tuning can potentially save a huge amount of time especially if the
process happens multiple times. Training an AI is almost always the slowest and most
expensive part and if there is a possibility to do it only once, why not. One example
of a fine-tuning could be a LLM that is pre-trained on general text data and then is
fine-tuned to translating text.

### d.
Masked Languge Model is trained by masking one token and then figuring out the missing 
token from the surrounding tokens. This is ideal for example applications of the LLM 
that need to understand the text that is given to them. The disadvantage for MLM is that
the model is not made to generate text as the model predicts the next token in parallel
which is not ideal if you want to generate one complete and coherent sentence. MLM are
best used to tasks like text classification.

Causal Languge Model is trained by analyzing the preceeding tokens which loses some
context compared to MLM. The tradeback is that CLM is especially made for generating new
text and can do that better than MLMs. A common use case for CLM is a chat-bot.

### e.


## 4

### a.
The chatbot should be classified as high risk system. This is because in the definition
of a high-risk system in the EU AI Act it is mentioned that an AI system that could
negatively affect the health and safety of people if they fail (or are misused) 
should be classified as high-risk systems. In this case the chatbot could and did
negatively impact vulnerable people by suggesting tips to losing weight.

In this case there are nine steps that need to be taken.
1. The risks should be foremost identified which probably was not done because this
should have been one clear risk assosiated with a chatbot like this.
2. Only datasets that contain the appropriate data should have been used in this model.
For example all data containing dieting and losing weight should be removed from the 
training data.
3. A safeguard should be formulated that the chatbot cannot give such negative answers.
4. Energy efficiency of the model should be improved.
5. Clear documentation to downstream providers should be provided. 
6. Establish a "Quality Management System" to manage the quality of the model.
7. Register the model to a EU database.
8. Keep documentation for 10 years from the launch to markets.
9. Compliance to other obligations including:
    * Proper transparency about the model and training data
    * Safeguards that it doesn't break law

### b.

1. Societal problem with AIs are social media algorithms. They are now implemented
as AI models to maximise engagement on a site. This is bad for multiple reasons. 
One is that there is the filter bubbling and the polarisation of people, as feeding content 
matching your views and values or content that is completely against it. This divides 
people into groups and sets them against each other which is a larger societal problem.
Also especially younger people are fed practically impossible standards that they
should reach to be "successful" for example money earned or looks which wreaks mental
health for many.
2. Another problem is misinformation which is very easy to create with AI. These models
are used for creating huge masses of "news" and other posts that contain fake information
sometimes by accident but sometimes not. This takes the spotlight of the real news
and facts that get buried under the sea of mis/disinformation.
3. AI models can be and are utilized by criminals. Scamming is made orders of magnitude
easier by LLMs. Before a scam message could often be recognized by poor english and other
errors but these are not prevalent in a message written by AI.
4. Training AI models are also very heavy on electricity use. Especially the training part
of many models takes up a huge amount of energy. In general for a generative AI model
with 7B parameters the training would consume 50 MWh of energy + 5MWh of validation and
inference only 0.1MWh/million requests.
5. Also the use of AI in a war machine raises questions about what descicions an AI can
make on the life of a human. Should an AI be able to kill a human and under which 
circumstances.
