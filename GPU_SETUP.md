# CUDA GPU Acceleration Setup for Ollama

## Your System
- **GPU**: NVIDIA GeForce RTX 3050 Laptop (4GB VRAM)
- **OS**: Windows

## Quick Setup

### Option 1: Use the Batch Script (Easiest)
Run the `start_ollama_gpu.bat` file to start Ollama with GPU support enabled.

### Option 2: Manual Setup

1. **Install NVIDIA CUDA Toolkit** (if not already installed):
   - Download from: https://developer.nvidia.com/cuda-downloads
   - Choose Windows, your architecture, and latest CUDA version
   - Install with default settings

2. **Verify CUDA Installation**:
   ```powershell
   # In PowerShell, run:
   nvcc --version
   ```

3. **Enable GPU in Ollama**:
   ```powershell
   # Set environment variables:
   $env:OLLAMA_GPU_LAYERS='all'
   $env:CUDA_VISIBLE_DEVICES='0'
   
   # Then start Ollama:
   ollama serve
   ```

4. **Run the Script**:
   ```powershell
   python summarize_sector_6.py
   ```

## Expected Performance Improvement

- **CPU Only**: ~18 minutes for 491 summaries (current)
- **GPU with CUDA**: ~2-4 minutes (4-9x faster)
- **Speedup Factor**: 4-9x depending on batch size and GPU utilization

## Troubleshooting

### GPU Not Detected
```powershell
# Check if CUDA is available:
ollama list
# Look for GPU memory allocation in output

# Or check with nvidia-smi (if installed):
# This requires NVIDIA GPU drivers properly installed
```

### Still Using CPU
- Ensure OLLAMA_GPU_LAYERS environment variable is set to 'all'
- Check Task Manager: GPU should show usage during inference
- Restart Ollama after setting environment variables

### Gemma3:1b Model Too Large for 4GB GPU
If you get out-of-memory errors:
- Use a smaller model: `phi3:mini` (2.2GB)
- Reduce GPU_LAYERS: Set to 20-30 instead of 'all'
- Keep using CPU (slower but works)

## GPU Layer Configuration

```
OLLAMA_GPU_LAYERS='all'      # Load entire model to GPU (fastest)
OLLAMA_GPU_LAYERS=32         # Load 32 layers to GPU
OLLAMA_GPU_LAYERS=16         # Load 16 layers to GPU (mixed CPU/GPU)
```

For RTX 3050 (4GB), try starting with 16-20 layers if 'all' causes memory issues.
