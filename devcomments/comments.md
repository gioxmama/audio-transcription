Um die Anwendung auf einem Linux-Server mit einer AMD-GPU auszuführen, müssen Sie einige Änderungen vornehmen, um ROCm (Radeon Open Compute) anstelle von CUDA zu verwenden. Hier sind die Schritte, die Sie befolgen sollten:

1. **ROCm installieren**:
   Folgen Sie den Anweisungen zur Installation von ROCm auf der offiziellen ROCm-Website: [ROCm Installation Guide](https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html).

2. **PyTorch mit ROCm installieren**:
   Installieren Sie PyTorch mit ROCm-Unterstützung. Sie können dies mit Conda tun:
   
```
   conda install pytorch torchvision torchaudio -c pytorch-nightly -c nvidia
   
```

3. **Ändern Sie die `DEVICE`-Einstellung in Ihrer `.env`-Datei**:
   Stellen Sie sicher, dass `DEVICE` auf `rocm` gesetzt ist:
   
```
   DEVICE = "rocm"
   
```

4. **Anpassen der Installationsanweisungen**:
   Ändern Sie die Installationsanweisungen in Ihrer `README.md`, um ROCm anstelle von CUDA zu verwenden. Hier ist ein Beispiel:

   
```markdown
   ### Installation
   - Stellen Sie sicher, dass Sie einen kompatiblen AMD-Treiber und ROCm-Version installiert haben: https://rocmdocs.amd.com/en/latest/Installation_Guide/Installation-Guide.html
   - Installieren Sie ffmpeg
       - Linux (Ubuntu): `sudo apt install ffmpeg`
   - Installieren Sie conda
       - Linux (Ubuntu):
           - `mkdir -p ~/miniconda3`
           - `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh`
           - `bash ~/miniconda3/miniconda.sh -u`
           - `rm ~/miniconda3/miniconda.sh`
           - Schließen und öffnen Sie Ihre aktuelle Shell erneut.
   - Erstellen Sie eine neue Python-Umgebung, z.B.: `conda create --name transcribo python=3.10`
   - Aktivieren Sie Ihre neue Umgebung: `conda activate transcribo`
   - Klonen Sie dieses Repository.
   - Installieren Sie die Pakete:
       - `conda install pytorch torchvision torchaudio -c pytorch-nightly -c nvidia`
       - `pip install -r requirements.txt`
   
```

5. **Überprüfen Sie die Kompatibilität der restlichen Abhängigkeiten**:
   Stellen Sie sicher, dass alle anderen Abhängigkeiten und Pakete, die Sie verwenden, mit ROCm kompatibel sind.

Nachdem Sie diese Änderungen vorgenommen haben, sollten Sie in der Lage sein, die Anwendung auf einem Linux-Server mit einer AMD-GPU und ROCm auszuführen.