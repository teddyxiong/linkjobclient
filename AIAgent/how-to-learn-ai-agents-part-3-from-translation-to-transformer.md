# How to Learn AI Agents (Part 3): From Translation to the Transformer

**Source:** [@Tedli8](https://x.com/Tedli8/status/2100450107242201240)

Recognition and generation are two important categories of AI tasks. Deep learning first made breakthroughs in image recognition, then changed the way machines process language. Today CNNs are still widely used in vision tasks, and Vision Transformers (ViT) let images be fed to a Transformer as sequences. But "recognizing what's in an image" and "generating a coherent sentence" are not the same problem.

To understand how language generation got to where it is today, machine translation is a good starting point.

## From Translation to the Transformer

The Bible tells the story of the Tower of Babel: people originally spoke one language, then were scattered to different places, and languages diverged. Placing it here neatly introduces the dilemma of machine translation: how do you re-express the same meaning in another language?

Translation isn't a word-by-word dictionary lookup. Different languages have different word orders, conventions, and expression lengths. A more appropriate modeling approach is sequence-to-sequence (seq2seq): take one sequence in, generate another out. Early statistical machine translation relied on large bilingual corpora, phrase correspondences, and probabilistic models, rather than simply replacing each word individually.

Neural networks brought a new idea: first represent words as vectors, then let the model learn the relationships between words from data. Word2Vec's classic illustration is "king − man + woman ≈ queen." This doesn't mean words can actually be arithmetically computed like numbers; it means the trained vector space can capture certain semantic relationships.

Next is the RNN. It's like a chain passing a note along: read one word, merge it with the previous hidden state, and pass it to the next position. Given "I love you," the model updates its state step by step; in theory, the final state summarizes the whole sentence.

Early neural machine translation used an encoder–decoder: the encoder reads the source language and compresses the information into a fixed-length context vector; the decoder then starts from that vector and generates the target language word by word. The design is elegant, but has an obvious bottleneck — the longer the sentence, the harder it is to fit all the details into a single vector.

RNNs also have training difficulties: information and gradients must propagate layer by layer along time steps, so long-range dependencies weaken easily. LSTM and GRU use gating mechanisms to decide what to keep, forget, and write, significantly alleviating the problem — but they don't make long-sequence tasks effortless.

Attention asked a different question: when generating the current target word, you don't have to rely only on the encoder's last state; instead look back at each position of the source sentence and give higher weight to the relevant parts. For example, translating "我昨天在北京见了她" ("I met her in Beijing yesterday") into English, when generating the location you focus on "北京," and when generating the time you look at "昨天." It alleviates the fixed-vector bottleneck and lets the model use distant information more directly.

Figure 1 can be read this way: RNNs transmit mainly along word order; the traditional encoder–decoder Attention lets the decoder look at the source sentence on demand; the Transformer goes further, letting different positions within the same sequence connect directly.

The 2017 paper "Attention Is All You Need" proposed the Transformer: in sequence modeling it no longer relies on the RNN's step-by-step recursion, but centers on self-attention, combined with feed-forward networks, residual connections, normalization, and positional information. Because there's no constraint that "you must first compute the previous word's hidden state before the next," training parallelizes more easily. Note that this refers to computing sequence representations during training; when an autoregressive model generates answers, it still generally outputs token by token.

Two far-reaching lines followed: BERT leaned toward bidirectional understanding, and GPT leaned toward continuing generation from existing context. They aren't the whole of the Transformer, but they showed that the same architecture can serve different tasks.

There's also an interesting idea: if different languages could share some intermediate representation, then in theory you could feed one language's encoding into another language's decoder. But whether it actually translates smoothly depends on shared representations, training method, and language alignment — you can't just casually splice different models' encoders and decoders together and expect it to work.

## The Path to Multimodality

Beyond language, image generation was also developing. The intuition of diffusion models can be viewed in reverse: during training, gradually add noise to a real image until the picture is almost pure noise; the model learns to recognize and remove noise at each step. During generation, start from noise, repeatedly denoise, and finally get a new image. It doesn't paint directly from a "blank canvas."

In Figure 2, the top row is the noising process and the bottom row is the generation that gradually restores from noise. The two rows look like mirror images, but generation is not playing the original image back in reverse — it's the model producing a new sample after learning the image distribution.

Text-to-image adds one more condition: the prompt. The encoded text participates in the denoising process, telling the model "what to generate." Taking the latent-space diffusion model behind Stable Diffusion as an example, a U-Net performs denoising, and cross-attention lets image features reference the text condition. Here Transformer-style attention is an important component, but you can't equate the whole diffusion model with a Transformer. Video generation usually also processes the time dimension to keep consecutive frames consistent.

As for "understanding images," ViT takes another path: split the image into small patches, map each patch to one token, and hand them to a Transformer for modeling. Multimodal LLMs still need a vision encoder, an alignment module, and training data to bring image information into the language model — it's not the case that merely concatenating image tokens with text tokens allows understanding everything.

From word sequences in translation, to patches in images, to video frames and other structured information, the key change is this: we began learning how to represent different modalities as model-processable sequences, and design training objectives that let the model build connections among these representations. The Transformer is powerful, but its capability still depends on data, task design, model structure, and compute resources.

## Summary

This installment originally aimed to cover connectionism, but ended up holding onto a single, easiest-to-follow thread: how translation drove seq2seq, Attention, and the Transformer, and how those ideas then entered vision and generation. Important details like residual connections are skipped for now — not because they don't matter, but because they're clearer when expanded separately.

The next installment will talk about behaviorism and reinforcement learning, from PPO and GRPO to Agent action and feedback. I'll try to explain intuition first, then technique, so this thread keeps connecting.