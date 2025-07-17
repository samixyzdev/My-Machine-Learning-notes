# 7/6/2025- [7/6/2025](#762025)
- [7/6/2025- 7/6/2025](#762025--762025)
- [1. **Datasets \& DataLoaders**](#1-datasets--dataloaders)
- [2. **Utils**](#2-utils)
- [7/7/2025](#772025)
- [7/8/2025](#782025)
- [7/14/2025](#7142025)
- [7/15/2025](#7152025)
- [7/16/2025](#7162025)
- [7/17/2025](#7172025)

**I finally decided to put some efforts into learning pytorch. I am writing this notes and making this public for anyone who are interest about me.**

# 1. **Datasets & DataLoaders**
labels_map = { // dictionary very understandable also an look up table
    0: "T-Shirt",
    1: "Trouser",
    2: "Pullover",
    3: "Dress",
    4: "Coat",
    5: "Sandal",
    6: "Shirt",
    7: "Sneaker",
    8: "Bag",
    9: "Ankle Boot", 
}
figure = plt.figure(figsize=(8, 8)) // creat a canvas
cols, rows = 3, 3
for i in range(1, cols * rows + 1):
    sample_idx = torch.randint(len(training_data), size=(1,)).item() 
    //torch.randint(N, size=(1,)) → random integer in [0, N − 1].
    //.item() converts the 1-element tensor to a plain Python int.
    img, label = training_data[sample_idx]
    figure.add_subplot(rows, cols, i)
    plt.title(labels_map[label])
    plt.axis("off")
    plt.imshow(img.squeeze(), cmap="gray")
plt.show()
train_dataset, val_dataset = random_split(dataset, [80, 20])
train_loader = DataLoader(dataset=train_dataset, batch_size=16)
val_loader = DataLoader(dataset=val_dataset, batch_size=20)
*loading one batch for each loop
# 2. **Utils**

too many funcitons, not so interesting.
Found another interesting blog, https://huggingface.co/blog/dvgodoy/beginner-pytorch-tutorial?utm_source=chatgpt.com.

# 7/7/2025

learned about the difference between GPU tensor and CPU tensor(Numpy)
" In PyTorch, every method that ends with an underscore (_) makes changes in-place, meaning, they will modify the underlying variable. "
torch.no_grad() : tell PyTorch to “back off” and let us update our parameters without messing up with its fancy dynamic computation graph

# 7/8/2025

finished my first ML competiton on Kaggle

# 7/14/2025

some C++ learning notes:
std:vector do not have push_front, I can only use insert(v.begin(), obj)

# 7/15/2025

some advanced usage of sort: assending order based on the second element

sort(points.begin(), points.end(),
     [](const vector<int>& a, const vector<int>& b) {
         return a[1] < b[1];
     });

# 7/16/2025
1. **I resubmited two codes for the titanic competition and scored around 0.8, a huge improvement from what I did from the last time**
2. **BERT for beginner**
   1. Token embeddings: A [CLS] token is added to the input word tokens at the beginning of the first sentence and a [SEP] token is inserted at the end of each sentence.
   2. Segment embeddings:A marker indicating Sentence A or Sentence B is added to each token. This allows the encoder to distinguish between sentences.
   3. Positional embeddings:A positional embedding is added to each token to indicate its position in the sentence.

# 7/17/2025
I was trying to use a List in CPP as a stack, but I found out that I could only use std:vector or std:stack:
#include <vector>

std::vector<char> stack;
add elements：stack.push_back('(');
pop elements：stack.pop_back();
visit top：stack.back();

#include <stack>

std::stack<char> stack;

add elements：stack.push('(');
pop elements：stack.pop();
visit top：stack.top();