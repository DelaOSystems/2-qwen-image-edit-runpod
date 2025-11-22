# Use a modern Runpod PyTorch base image
FROM runpod/pytorch:1.0.2-cu1281-torch271-ubuntu2204

# Install dependencies
# Install dependencies (including latest diffusers from GitHub)
RUN pip install --no-cache-dir \
    "git+https://github.com/huggingface/diffusers.git" \
    "transformers>=4.51.3" \
    accelerate \
    safetensors \
    pillow \
    runpod \
    hf_transfer \
    bitsandbytes


# (Optional) Pre-download the model to reduce cold start latency
RUN python -c "from diffusers import DiffusionPipeline; DiffusionPipeline.from_pretrained('Qwen/Qwen-Image-Edit-2509')"

# Copy handler file
WORKDIR /app
COPY handler.py .

# Set entrypoint
CMD ["python", "handler.py"]
