#cybersecurity #hacking #networking #portscanning
#penetration-testing 

# Rust Scan

<iframe width="560" height="315" src="https://www.youtube.com/embed/HT5nQteKZeg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Notes:
- RustScan is infinitely faster than NMAP
- In order to get it working on my Kali Arm VM I had to build it from the source
- https://github.com/RustScan/RustScan

# Building Rust Scan from Source on an ARM64 Kali Machine

1. Install dependencies
```bash
sudo apt-get update && sudo apt-get install -y git build-essential libssl-dev
```
2. Clone the RustScan repository from Github
```bash
git clone https://github.com/RustScan/RustScan.git
```
3. Change to the RustScan directory
```bash
cd RustScan
```
4. Install an ARM64-compatible Rust toolchain
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --default-toolchain nightly --target aarch64-unknown-linux-gnu
```
5. Set the PATH environment variable to include the Rust toolchain's bin directory
```bash
export PATH="$HOME/.cargo/bin:$PATH"
```
6. Build RustScan
```bash
cargo build --release --target aarch64-unknown-linux-gnu
```
7. Copy the RustScan binary to a directory in your PATH
```bash
sudo cp target/aarch64-unknown-linux-gnu/release/rustscan /usr/local/bin/
```
8. Verify that RustScan is installed
```bash
rustscan --version
```

