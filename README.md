# Matrix-Net
A proof‑of‑concept platform where files are stored not as raw bytes but as tiny JSON “recipes” that point to a shared, immutable Matrix of public data blocks. By reconstructing content from this global matrix, MatrixNet achieves ultra‑compressed, censorship‑resistant distribution and enables offline browsing with only a few kilobytes per file.

**Recipe‑Based Decentralized Web**

A proof‑of‑concept platform that stores files as tiny *recipes* which reference a shared, immutable **Matrix** of public data blocks. By reconstructing content from this global matrix we achieve ultra‑compressed, censorship‑resistant distribution and enable offline browsing with only a few kilobytes per file.

---  

## Table of Contents
- [What is MatrixNet?](#what-is-matrixnet)
- [Key Features](#key-features)
- [Quick Start (Linux/macOS/Windows)](#quick-start)
- [Repository Layout](#repository-layout)
- [How It Works](#how-it-works)
- [Contributing & Community](#contributing--community)
- [Roadmap](#roadmap)
- [License](#license)

---  

## What is MatrixNet?

Instead of sending the raw bytes of a file, **MatrixNet**:

1. **Shares a single global data set** – the *Matrix* – built once from publicly licensed sources (Wikipedia dumps, GitHub archives, Project Gutenberg, etc.).  
2. Encodes any new file as a **Recipe** (JSON) that maps each 4 KB chunk of the original file to a block in the Matrix plus an optional tiny transformation (e.g., XOR mask).  
3. Allows any peer that already holds the Matrix to reconstruct the original file locally, even when offline.

> *“I’ve opened a GitHub repository where we can **build MatrixNet together** with the community—please join the discussion, file issues, and submit pull‑requests!”*  

---  

## Key Features

- **Hyper‑compressed distribution** – recipes are usually only a few KB regardless of original size.  
- **Censorship‑resistant & permanent** – as long as the Matrix exists somewhere, any recipe can be resurrected forever.  
- **Offline browsing** – with a local copy of the Matrix you can reconstruct any linked content without ever touching the network.  
- **Deterministic reconstruction** – same recipe + same matrix → identical output byte‑for‑byte.  
- **Extensible transformation layer** – currently XOR masks; future versions may support delta‑coding, byte‑reordering, or custom reversible ops.  

---  


## How It Works (high‑level)

1. **Matrix Generation** (`matrix_builder`)  
   - Crawl public, permissively‑licensed sources.  
   - Chunk every source into 4 KB blocks.  
   - Deduplicate → store each unique block once.  
   - Build a fast hash
