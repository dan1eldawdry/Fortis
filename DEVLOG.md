# DEVLOG

## 24 Nov
- Set up Ollama (gpt-oss:20b, qwen2.5-coder:14b, llama3.1:8b) and Continue in VS Code.
- Agent mode printed JSON instead of running, so I switched to Chat mode.
- gpt-oss gave empty answers. Fixed by raising contextLength to 16384.

## 26 Nov
- Forked Fortis and ran setup.ps1.
- Setup crashed at line 76 when pip uninstalled llama_cpp_python. Wrapped the uninstall lines in Invoke-Native. Fixed.
- qwen and gpt-oss both suggested fixes for the crash that were partly wrong.
- 10 report tests failed on the first run, then passed on every run after. Can't reproduce.
- llama.cpp fell back to CPU instead of using the GPU.

## 29 Nov
- Setup passes all 239 tests and Fortis opens.
- Checked chat, an ISO 27001 question, a firewall config review and a DOCX report. All work.
- Problems in the answers: wrong ISO control numbers, says "you uploaded" when I didn't, severity counts don't match, the word "High" turns into a badge.
- Four models downloaded because I clicked other tiers by accident.

## 02 Dec
- Open reports folder button does nothing.
- Installed llama.cpp by hand to see the real GPU error. llama.dll couldn't load because the CUDA files were missing.
- Installed CUDA Toolkit 12.8. GPU now works and nvidia-smi shows Fortis using it.
- Ollama has to be stopped first, or Fortis only puts part of the model on the GPU.

## 03 Dec
- gpt-oss was wrong about Python versions and Store Python.
- The tests overwrite my selected model with a fake test file, so the first chat after setup fails.
- Stage 1 done.

## To do
- Stage 2: wrong ISO numbers, "you uploaded" problem, severity counts, badge bug, Fortis contacting huggingface.co every start.
- Stage 3: Torch still on CPU, reports folder button, tests overwriting my model, put the CUDA fix into setup.ps1.