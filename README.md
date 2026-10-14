# Awesome-Vision-Language-Action-Models

# Top Vision-Language-Action Models Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Generalist Robot Policies, Language-Conditioned Control & Cross-Embodiment Transfer*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Vision-Language-Action (VLA) Models**. These models combine visual perception, natural language understanding, and motor action generation into unified policies that can follow open-ended instructions, generalize to novel objects, and control robots across different embodiments.

**Examples** include OpenVLA, RT-2 (DeepMind), Octo Model, RT-1, PaLM-E, Covariant RFM-1, Physical Intelligence π₀, GR-1, VoxPoser, and RoboFlamingo (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom fine-tuning, and transparent robot learning — ideal for robotics researchers, embodied AI developers, and labs building generalist manipulation policies on consumer hardware.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Physical Intelligence π₀](https://www.physicalintelligence.company/)**  
  Commercial VLA foundation model with Flow Matching action generation. Trained on 10,000+ hours of robot data across 7 robot configurations and 68 tasks. Not open-source; available via API and partnership. Notably fast training (5 hours on 4×H100 for the “speed run” variant) and strong out-of-the-box performance on complex tasks .

- **[Covariant RFM-1](https://covariant.ai/rfm/)**  
  Robotics Foundation Model for warehouse operations, combining real-world robot data with internet-scale text. Series C funding ($222M). Positioned as a commercial foundation model for logistics and industrial automation .

- **[Google DeepMind RT-2](https://deepmind.google/discover/blog/rt-2-new-model-translates-vision-and-language-into-action/)**  
  Vision-language-action model built on PaLI-X (55B) and PaLM-E backbones. Demonstrates emergent semantic reasoning (e.g., “pick up the bag about to fall off the table”). Not open-source; research demo only .

- **[Google PaLM-E](https://research.google/blog/palm-e-an-embodied-multimodal-language-model/)**  
  562B-parameter embodied multimodal language model. Inputs include images, robot states, and text; outputs text-based decisions. State-of-the-art on OK-VQA. Not open-source .

- **[Google RT-1](https://robotics-transformer1.github.io/)**  
  Robotics Transformer for multi-task manipulation, trained on 130K episodes across 700 tasks. Foundation for RT-2. Not open-source .

## Open-Source GitHub Projects

- **[OpenVLA](https://github.com/openvla/openvla)**  
  **The leading fully open-source VLA**: 7B-parameter model based on Llama-2 with fused DINOv2 + SigLIP vision encoders. Trained on 970K real-world robot demonstrations from Open X-Embodiment. **Outperforms the 55B RT-2-X by 16.5% absolute task success rate** across 29 tasks and multiple embodiments, with 7× fewer parameters. Supports LoRA fine-tuning on consumer GPUs and quantization for efficient serving. MIT licensed .

- **[Octo](https://github.com/octo-models/octo)**  
  Open-source generalist robot policy: transformer-based diffusion policy trained on 800K trajectories from Open X-Embodiment. Available in **Octo-Base (93M params, 13 it/sec on RTX 4090)** and **Octo-Small (27M params, 17 it/sec)** . Supports multiple RGB cameras, language or goal-image conditioning, and flexible action spaces. **Fastest fine-tuning of any model**: 30 minutes to 2 hours on a single GPU. MIT licensed .

- **[OpenVLA (LoRA Fine-Tuning)](https://github.com/openvla/openvla)**  
  Official LoRA fine-tuning notebooks and PyTorch codebase for adapting OpenVLA to new robots and tasks on consumer hardware. Includes training scripts for Open X-Embodiment datasets .

- **[RoboFlamingo](https://github.com/RoboFlamingo/RoboFlamingo)**  
  Open-source VLA built on OpenFlamingo (MPT-7B backbone) with perceiver resampler for temporal visual reasoning. **State-of-the-art on CALVIN benchmark** for multi-step long-horizon tasks. Processes sequences of frames rather than single frames, giving advantage on tasks requiring memory. 9B parameters; fine-tuning requires 2×A100 .

- **[RoboFlamingo-Plus](https://github.com/RoboFlamingo/RoboFlamingo-Plus)**  
  Enhanced version fusing **depth and RGB perception** with VLMs. Achieves 10–20% improvement over RoboFlamingo on manipulation tasks. Uses pre-trained ViT with resampling, depth feature extraction, and cross-attention for optimal feature integration .

- **[GR-1](https://github.com/bytedance/GR-1)**  
  Open-source VLA from ByteDance using **video generative pre-training** for robot manipulation. Trained to predict delta XYZ positions and delta Euler angles for arm actions with binary gripper actions. Demonstrates strong generalization to unseen language instructions .

- **[VoxPoser](https://github.com/huangwl18/VoxPoser)**  
  Open-source framework that **leverages LLMs for open-world reasoning and VLMs for visual grounding** in a model-based planning approach. Grounds language instructions directly in 3D observation space with real-time visual feedback. Enables zero-shot generalization for open-set instructions and objects without robot data .

- **[SmolVLA](https://github.com/huggingface/smolvla)**  
  Hugging Face’s **smallest and fastest open-source VLA**. Achieves **82–90% success on LIBERO** — within 5% of OpenVLA despite **16× fewer parameters**. Runs at **15–30 Hz on a single RTX 4090**. Full fine-tuning on 200 demonstrations takes 4–12 hours. Ideal for labs with consumer GPUs .

### Additional Strong Open-Source Options

- **[Open X-Embodiment Dataset](https://robotics-transformer-x.github.io/)** — The foundational dataset for nearly all open-source VLAs: ~970K trajectories across 22 embodiments. Essential for training and benchmarking .
- **[MuJoCo](https://github.com/google-deepmind/mujoco)** — Free, open-source physics simulator for robotics research. Widely used for VLA evaluation and training .
- **[π₀ PyTorch Implementation](https://pypi.org/project/pi-zero-pytorch/)** — Community PyTorch reimplementation of Physical Intelligence’s π₀ Flow Matching model, released under open license .
- **[OpenVLA Fine-Tuning Notebooks](https://github.com/openvla/openvla)** — Official notebooks for LoRA and full fine-tuning on custom robot data.
- **Simulators** — MuJoCo, Isaac Sim, PyBullet for VLA training and evaluation environments.

**Frameworks for building custom systems**: Combine **OpenVLA** for strong language grounding, **Octo** for rapid fine-tuning and diffusion action generation, **SmolVLA** for consumer-GPU deployment, **RoboFlamingo** for long-horizon temporal reasoning, and **VoxPoser** for zero-shot LLM-guided planning to build a complete open-source VLA stack.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- VLA models must comply with robot safety standards, ethical AI guidelines for autonomous systems, and applicable robotics regulations.
- Self-hosted open-source solutions require proper GPU infrastructure, robot safety validation, and ongoing model monitoring.

---

**Made for robotics researchers, embodied AI developers, manipulation engineers, and labs building generalist robot policies.**  
Let's make Vision-Language-Action models more open, accessible, and robot-friendly.
