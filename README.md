# Amazon EFS Utils for Debian 13 - Transparent builds

**Debian 13 (trixie) packages of the official AWS Elastic File System and S3 Utilities**

This repository automatically builds and publishes clean, verified `.deb` packages of [`amazon-efs-utils`](https://github.com/aws/efs-utils) for Debian 13.

- **Upstream version**: Always tracks the latest official AWS release
- **Built every 6 hours** with full verification on a real Debian 13 container
- **GCC 13 + modern Rust** (required for current AWS SDK crates)
- **TRANSPARENCY**: no modifications to the upstream code. You can always check the github action workflow file which produces the build

---

### 📥 Downloads

| Package | Link | Description |
|---------|------|-------------|
| **Latest** | [amazon-efs-utils-latest.debian13_amd64.deb](https://github.com/the-ar-chitect/aws-efs-utils-debian/releases/download/amazon-efs-utils-debian13/amazon-efs-utils-latest.debian13_amd64.deb) | Always points to the newest build (stable URL) |
| Previous versions | [releases page](https://github.com/the-ar-chitect/aws-efs-utils-debian/releases) | All historical builds are kept in the “Latest” release for easy access. |


---

### 🚀 Quick Install

```bash
# 1. Download the latest package
wget https://github.com/the-ar-chitect/aws-efs-utils-debian/releases/download/amazon-efs-utils-debian13/amazon-efs-utils-latest.debian13_amd64.deb

# 2. Install
sudo apt-get install -y ./amazon-efs-utils-latest.debian13_amd64.deb

# 3. (Optional) Configure region
sudo mkdir -p /etc/amazon/efs
sudo tee /etc/amazon/efs/efs-utils.conf > /dev/null <<EOF
[default]
region = us-east-1
EOF
```

Now you can mount EFS the normal way:

```bash
sudo mkdir -p /mnt/efs
sudo mount -t efs -o tls fs-12345678:/ /mnt/efs
```

---

### 🔧 How It Works

- GitHub Actions runs every 6 hours (and on manual trigger)
- Automatically detects new upstream versions from AWS
- Builds inside a clean `debian:trixie` container
- Applies the correct `1.debian13` release suffix
- Runs full install + binary verification
- Publishes both a versioned release **and** updates the stable “latest” release

---

### 🛠️ Building Locally

If you want to build it yourself:

```bash
git clone https://github.com/the-ar-chitect/aws-efs-utils-debian.git
cd aws-efs-utils-debian
# (see .github/workflows/build-efs-utils.yml for the exact steps)
```

---

### 📜 License

- The packages are built from the official [`amazon-efs-utils`](https://github.com/aws/efs-utils) which is licensed under the [Apache License 2.0](https://github.com/aws/efs-utils/blob/master/LICENSE).
- This repository (the build automation) is also Apache 2.0.

---

### 🙏 Credits

- Official AWS EFS Utils: [aws/efs-utils](https://github.com/aws/efs-utils)
- Built and maintained with ❤️ using GitHub Actions

---

**Questions or issues?** Open an issue or just ping me — happy to help!
