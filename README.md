# Poseidon2 Hashing with Multiprocessing

## Overview
This is a Python implementation of the **Poseidon2 hash function** and **Merkle tree** with the support of **multiprocessing** for a performance boost. The program applies **Montgomery reduction**, an **S-box transformation**, an **MDS matrix-based linear layer**, and a **Merkle tree computation** for efficient hashing of input data.

## Features
- **Poseidon2 Hash Function**: Zero-knowledge proof (ZKP) optimized cryptographic hash function.
- **Montgomery Reduction**: Quick modular arithmetic with the prime `2^255 - 19`.
- **Merkle Tree Construction**: Builds a Merkle root from computed hashes.
- **Parallel Processing**: Uses Python's `multiprocessing` to parallelize input data processing.

## Dependencies
**Python 3** and the standard library's `multiprocessing` module are the only dependencies for this script. There are no third-party dependencies.

## How It Works
1. **Splitting Data into Chunks**
- The input data is split into chunks of size `t` (default `t = 3`).
2. **Parallel Hash Computation**
   - The script spawns multiple worker processes to compute hashes concurrently.
3. **Merkle Tree Construction**
   - The computed hashes are used to build a **Merkle tree**, yielding a single Merkle root.
4. **Printing Results**
- Computed hashes and final Merkle root are displayed in hexadecimal.

## Code Structure
### Key Functions
- `montgomery_reduction(x)`: Conducts Montgomery reduction.
- `s_box(value)`: Applies the Poseidon2 S-box transformation.
- `apply_round_constants(state, round_constants)`: Adds round constants.
- `apply_linear_layer(state, mds_matrix)`: Applies the MDS matrix transformation.
- `poseidon2_permutation(state, mds_matrix, round_constants)`: Runs the Poseidon2 permutation.
- `poseidon2_hash(input_data)`: Calculates the Poseidon2 hash for the given input data.
- `compute_merkle_root(hashes)`: Constructs the Merkle tree and returns the root.

### Parallel Processing
- `process_chunk(chunk_id, chunk)`: Computes the Poseidon2 hash of a chunk.
- `worker(chunk_queue, result_queue)`: Worker function for multiprocessing.

## Usage
Run the script using:
```bash
python poseidon2_hash.py
```

### Example Input
```python
input_data = [42, 77, 33, 55, 66, 78, 88, 99, 10, 20, 30, 40, 40, 40, 30]
```

### Example Output
```bash
Computed Hashes:
Chunk 1: 1107617496CF4DDE3FE54231FCA67F1EFA5C3962CFD49B06CB8ED4AC8FC350FF
Chunk 2: 3315CA7C8A49405A46847E51BCC14EBE17831209939884C693FC0555FC757FC5
Chunk 3: 23F61BBB498C3C92B3ADA598AB81C8ED23C1697274DA07C81C7C70DD82B61099
Chunk 4: 3A1A0A3A43D15BC79AEFD42C249189B957E9056FA653AAC96D03FAB1C950A504
Chunk 5: 3804C6B680BAD2EBA72105662AE96C6D472964F1EEE4DF86A7F91AC2317F7C75
Merkle Root: 3B679066991E602999BA9E2783F42F0CEC0AF3480450006C1F6A3B6C1DBFF2A8


#
