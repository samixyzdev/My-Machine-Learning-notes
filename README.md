7/6/2025
I finally decided to put some efforts into learning pytorch. I am writing this notes and making this public for anyone who are interest about me.
Here is the website that I use: https://docs.pytorch.org/tutorials/beginner/basics/data_tutorial.html

1. Datasets & DataLoaders
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

2. Utils
too many funcitons, not so interesting.
Found another interesting blog, https://huggingface.co/blog/dvgodoy/beginner-pytorch-tutorial?utm_source=chatgpt.com.

7/7/2025
learned about the difference between GPU tensor and CPU tensor(Numpy)
" In PyTorch, every method that ends with an underscore (_) makes changes in-place, meaning, they will modify the underlying variable. "
torch.no_grad() : tell PyTorch to “back off” and let us update our parameters without messing up with its fancy dynamic computation graph