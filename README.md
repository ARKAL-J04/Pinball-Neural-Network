🏓 Pinball Neural Network (PNN)

A Lightweight, Topology-Driven Sparse Neural Network for TinyML and Edge Computing

📌 Overview (معرفی پروژه)

The Pinball Neural Network (PNN) is a custom, highly sparse neural network architecture designed for resource-constrained environments like Microcontrollers (Arduino, STM32) and IoT devices.

Instead of traditional Fully Connected (Dense) layers, PNN uses Geometric Masking. Neurons are arranged in specific shapes (Triangles, Hexagons) and information "bounces" within these boundaries, similar to a pinball machine. This forces the network to learn deep, robust features with a fraction of the parameters.

📐 Topology Experiments (نبرد هندسه‌ها)

We conducted extensive ablation studies to find the optimal geometric routing for the information flow:

The Triangle (30 Nodes | 600 Links): Highly stable, acts as a strong regularizer.

The Square (32 Nodes | 768 Links): Fast convergence but computationally heavier.

The Hexagon (24 Nodes | 480 Links) 🏆: The ultimate winner. Despite having 20% fewer connections than the triangle, its high Path Diversity (5 routing options per node) allows it to achieve state-of-the-art accuracy with the lowest inference time.

🏢 The Pinball Tower & ResNet (برج پینبال و اتصالات میان‌بر)

To handle more complex datasets, we designed the Pinball Tower, a 4-story hierarchical architecture:

Floor 0: Triangle (30 Nodes)

Floor 1: Hexagon (24 Nodes)

Floor 2 (Bottleneck): Triangle (15 Nodes)

Floor 3: Hexagon (24 Nodes)

Challenge: Expanding the depth caused the Vanishing Gradient problem, dropping accuracy to a mere 7.78%.
Solution: By implementing Residual (Skip) Connections (both local layer-wise and global), we successfully bypassed the dead ReLU nodes. The accuracy skyrocketed back to 96.39%, proving the necessity of ResNet topology in sparse deep networks.

📊 Benchmark Results (نتایج ارزیابی)

Fashion-MNIST Challenge

The Deep Residual Pinball Tower was tested against the complex Fashion-MNIST dataset (28x28 images).

Epochs: 15

Training Time: ~3 Minutes (on standard CPU)

Final Test Accuracy: 86.47%

Conclusion: The model successfully extracts complex features (differentiating coats, sneakers, shirts) with an extremely sparse parameter footprint, proving its high Information Efficiency.

🚀 Quick Start (راهنمای اجرا)

Prerequisites

Python 3.8+

PyTorch

Torchvision

Matplotlib & Scikit-Learn

Running the Models

To run the Topology Battle (Triangle vs Square vs Hexagon):

python topology_battle.py


To run the Ultimate ResNet Tower Battle:

python pinball_ultimate.py


To test the architecture on real-world data (Fashion-MNIST):

python fashion_mnist_pinball.py


🛠️ Why Pinball NN? (کاربردها در دنیای واقعی)

Microcontrollers (TinyML): The Hexagon architecture requires storing only 480 weights instead of thousands, saving precious Flash memory.

Low Latency: Fewer multiplication operations (MACs) lead to drastically faster C/C++ inference times on embedded systems.

Green AI: Trains quickly on CPUs without the need for expensive GPU clusters.

Architected and Researched as a modern approach to Sparse Neural Networks.
