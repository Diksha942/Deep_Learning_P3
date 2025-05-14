# Adversarial Attacks on Pretrained ResNet-34 and Transferability Study

This project demonstrates adversarial attacks (FGSM, BIM, Patch Attack) on a **pretrained ResNet-34** model trained on ImageNet-1K.
We also study **transferability** of these attacks by evaluating them on a second model — **DenseNet-121**.

---

## 🛠 Project Structure

* **Dataset**: Subset of ImageNet-1K classes, packaged in `TestDataSet.zip`.
* **Model**: Pretrained ResNet-34 (`torchvision.models.resnet34`).
* **Attacks Implemented**:

  * **FGSM** (Fast Gradient Sign Method) — one-step attack.
  * **BIM** (Basic Iterative Method) — iterative FGSM attack.
  * **Patch Attack** — perturbing only a small 32×32 patch in the image.
* **Evaluation**:

  * Performance evaluated using **Top-1** and **Top-5** accuracy.
  * Adversarial examples are saved in organized folders.
  * Visualizations showing clean vs adversarial comparisons.
* **Transferability**:

  * The generated adversarial examples are evaluated on **DenseNet-121** to test attack generalization across models.

---

## 🚀 How to Run

1. **Upload** your dataset:

   * When prompted by the script, upload your `TestDataSet.zip` file.
   * **Structure required inside zip**: Folder per class (compatible with `torchvision.datasets.ImageFolder`).
   * Make sure a `labels_list.json` is present to map dataset classes to ImageNet indices.
2. **After upload**, the script will automatically:

   * Unzip and load the dataset.
   * Preprocess images (normalize as per ImageNet standards).
   * Evaluate the pretrained ResNet-34 on clean data.
   * Generate adversarial datasets using:

     * FGSM
     * BIM
     * Patch Attack
   * Save perturbed images into new folders.
   * Evaluate adversarial transferability on DenseNet-121.
   * Visualize example adversarial images.

✅ No manual intervention needed after the file upload.

---

## 🧠 Core Concepts Covered

* **Adversarial Attack**: Tiny perturbations that fool deep learning models.
* **Fast Gradient Sign Method (FGSM)**: Quick and cheap attack using the sign of gradients.
* **Basic Iterative Method (BIM)**: Stronger, multi-step version of FGSM.
* **Patch Attacks**: Confining adversarial changes to small local areas.
* **Transferability**: How adversarial examples built for one model affect another model.

---

## 📂 Output Structure

* `/TestDataSet/` → Clean dataset (unzipped from your uploaded file)
* `/Adversarial_Test_Set1/` → Images perturbed using FGSM
* `/Adversarial_Test_Set2/` → Images perturbed using BIM
* `/Adversarial_Test_Set3/` → Images perturbed using Patch Attack (32×32 patch)

Each adversarial dataset maintains the original class folder structure.

---

## 📊 Expected Results =

| Task                      | Top-1 Accuracy | Top-5 Accuracy |
| ------------------------- | -------------- | -------------- |
| **Clean Images** (Task 1) | 76.00%         | 94.20%         |
| **FGSM Attack** (Task 2)  | 3.60%          | 20.80%         |
| **BIM Attack** (Task 3)   | 0.00%          | 1.80%          |
| **Patch Attack** (Task 4) | 8.80%          | 25.40%         |


---

| Dataset                        | Top-1 Accuracy | Top-5 Accuracy |
| ------------------------------ | -------------- | -------------- |
| **Original Clean Images**      | 74.60%         | 93.60%         |
| **Adv 1 (FGSM Attack)**        | 51.20%         | 79.00%         |
| **Adv 2 (Iterative FGSM)**     | 65.80%         | 91.40%         |
| **Adv 3 (Patch-32×32 Attack)** | 70.40%         | 92.00%         |


## ✨ Technologies Used

* [PyTorch](https://pytorch.org/)
* [Torchvision](https://pytorch.org/vision/)
* [Google Colab](https://colab.research.google.com/)
* [Matplotlib](https://matplotlib.org/)
* [TQDM](https://github.com/tqdm/tqdm)

---

## 📋 Requirements

You can run this project in **Google Colab** (recommended) — no local setup needed.
If running locally, install:

```bash
pip install torch torchvision matplotlib tqdm
```

---

## 📝 License

This project is for educational and research purposes only.
Feel free to fork, experiment, and extend!

---

# 📢 Important Note

⚡ **You MUST manually upload `TestDataSet.zip`** when the script prompts for file upload.
Without this, the notebook will not proceed.
