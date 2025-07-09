### 📄 **`chrome-remote-debug/README.md`**

````markdown
# Chrome Remote Debug

Run Google Chrome inside a Neko container with remote debugging enabled and accessible from a browser. This app is useful for testing, automation, and accessing Chrome DevTools externally.

---

## 🚀 Build

Clone the `neko-apps` repository and build the image:  

```bash
git clone https://github.com/m1k1o/neko-apps.git
cd neko-apps

./build --application chrome-remote-debug --base_image ghcr.io/m1k1o/neko/base:latest
````

The image will be tagged as:

```
ghcr.io/m1k1o/neko-apps/chrome-remote-debug:latest
```

---

## ▶️ Run

Run the container with the following command:

```bash
docker run -it --rm \
  -p 8080:8080 \
  -p 9223:9223 \
  --shm-size=2gb \
  --cap-add=SYS_ADMIN \
  ghcr.io/m1k1o/neko-apps/chrome-remote-debug:latest
```

This will:

* Expose the Neko web interface on port `8080`
* Expose Chrome DevTools on port `9223`

---

## ⚙️ Add Custom Chrome Flags

You can pass additional Chrome flags using the `NEKO_CHROME_FLAGS` environment variable. Example:

```bash
docker run -it --rm \
  -p 8080:8080 \
  -p 9223:9223 \
  --shm-size=2gb \
  --cap-add=SYS_ADMIN \
  -e NEKO_CHROME_FLAGS="--no-sandbox --no-zygote --disable-extensions --window-size=1920,1080" \
  ghcr.io/m1k1o/neko-apps/chrome-remote-debug:latest
```

---

## 🙏 Special Thanks

Thanks a ton [@Nefaris](https://github.com/Nefaris) 🙏!
Your [comment](https://github.com/m1k1o/neko/issues/391#issuecomment-3016080496) really helped me set this up successfully.

---

## 📖 Documentation

For more details about Neko apps and room management, see the [Neko Documentation](https://github.com/m1k1o/neko).

---