# BUDA Apps Portfolio

[Open the portfolio page](https://TashiRabten.github.io/BUDA_APPs_Port/)

This repository contains the public portfolio page of the BUDA applications. Recruiters can use the page to see the functions of each application.

## Purpose

For each BUDA application, the page gives a short description, a list of functions, and the tech stack. Most applications also have a video. The page also gives contact information.

The source code of the applications is in private repositories because of copyright.

## Projects

### TradutorBUDA

TradutorBUDA is a Java application for the translation of Tibetan Buddhist texts. It helps translators to find the correct Buddhist terms.

**Tech stack:** Java 21, Maven, SQLite, ONNX Runtime, tokenizers, NLLB and mBERT Transformer models, CNN OCR model, NumPy

**Functions**
- It finds Tibetan terms in the glossary and in dictionaries.
- It separates Tibetan text into words and changes Tibetan script into Latin letters.
- Machine learning models put the best results first.
- It can read scanned pages with an OCR engine.

[See the video](https://youtu.be/_ULlCKEIytM)

### GlossarioBUDA (Simplified)

GlossarioBUDA is a glossary application for Buddhist terms. This version has only the main glossary functions. It does not contain the OCR integration of the full version.

**Tech stack:** Java 21, SQLite, SWT, XML, Supabase real-time sync

**Functions**
- You can add, edit, delete, and search for Buddhist terms.
- It stores terms in Tibetan, Sanskrit, Pāli, English, and Portuguese.
- You can type Tibetan text in the SWT interface.
- It imports terms from XML files and exports them in a format for WhatsApp.
- A small window stays on top of other windows, so you can see the terms at all times.
- An SQLite database stores the terms.

[See the video](https://youtu.be/UUHd_YkNNaI)

### Tibetan OCR — CNN and Transformer Research

This deep learning project compares two neural network architectures for the OCR of Tibetan characters. One architecture is a small CNN. The other architecture is a hybrid of a CNN and a Transformer. The purpose is to replace hand-crafted OCR steps with features that convolution and attention layers learn from the data.

The result is **namsel_buda**, a new version of the original [Namsel OCR](https://github.com/thubtenrigzin/namsel-ocr) engine. It uses Python 3.12, the CNN recognizer of this project, and safe model formats that do not use pickle. TradutorBUDA uses namsel_buda as its Tibetan OCR engine. The engine changes scanned pages into Unicode text. You can then edit the text, find its terms in the dictionary, and translate it.

**Tech stack:** PyTorch, CNN, Transformer, ONNX, INT8 quantization, mixed-precision training, Gradio, Hugging Face Spaces

**Results**
- The validation accuracy is 95.52% on 1,020 classes of Tibetan characters.
- The project compares a small CNN with a hybrid of a CNN and a Transformer.
- The OCR engine is available as namsel_buda, a fork of Namsel OCR.

**Links**
- [See the presentation](https://youtu.be/UMSwbuFfDLk)
- [Test the model on Hugging Face Spaces](https://huggingface.co/spaces/trabten/tibetan-ocr)
- [namsel_buda on GitHub](https://github.com/TashiRabten/namsel-ocr)

### SuiteBUDA — Multi-Cloud Backup

SuiteBUDA has the functions that all BUDA applications use. Its data protection layer backs up the files of the applications to cloud services and to other disks. The layer does not contain a cloud library. It runs the rclone program with fixed commands.

The idea for this layer comes from [curate-d](https://github.com/jorgejch/curate-d), an open-source multi-cloud file organizer by jorgejch. The layer uses the same safety rule as curate-d. This rule is “copy, verify, then register”.

**Tech stack:** Java, rclone, rclone crypt, SHA-256, pCloud, Google Drive, OneDrive, Amazon S3

**Functions**
- The layer uses rclone to send copies to pCloud, Google Drive, OneDrive, Amazon S3, and other cloud services. It can also use another disk or a NAS.
- The layer records a copy only after it reads the copy back from the service and gets the same SHA-256 hash.
- The layer stores the content of each file only one time, under its SHA-256 hash. A file in many versions uses only one copy at each service.
- The layer copies an SQLite database only when no application writes to it.
- Each backup records a version. You can restore a version into a new folder. The restore does not overwrite the files of the applications.
- The layer can read all copies back and repair damaged copies from good copies. The layer never deletes files at a service.
- With an rclone crypt remote, the copies stay encrypted at the cloud service.
- The layer can also release disk space. It removes a local file that did not change for a specified number of days, but only after it reads each copy back. An index lets you put the file back.

## Contact

- Email: Tashi.Rabten.Programming@gmail.com
- GitHub: https://github.com/TashiRabten/
