# Sculpt4D — Project Page

Project page for **Sculpt4D: Generating 4D Shapes via Sparse-Attention Diffusion Transformers**.

Live site: [https://<user>.github.io/sculpt4d/](https://github.com/)

## Layout

```
.
├── index.html              # Main page
├── static/
│   ├── css/style.css       # Styles
│   ├── js/viewer.js        # Three.js PLY sequence viewer
│   ├── images/             # Paper figures (PNG)
│   ├── videos/             # Input videos
│   └── meshes/             # Per-case PLY sequences (frame_XXXX.ply)
└── README.md
```

## Local preview

```bash
python -m http.server 8000
```

Then open <http://localhost:8000/> in your browser. A local HTTP server is
required (opening `index.html` directly will not load the PLY meshes because
of browser origin restrictions).

## Deployment (GitHub Pages)

1. Push the repository to GitHub.
2. In the repo settings: **Settings → Pages → Source: `Deploy from a branch`
   → Branch: `main` → Folder: `/ (root)`**.
3. The site is live at `https://<user>.github.io/<repo>/` within a minute.

## Adding or removing cases

Edit `window.RESULTS_CONFIG_16` and `window.RESULTS_CONFIG_32` near the
bottom of `index.html`. Each entry:

```js
{
    id:          "<folder_under_static/meshes>",
    label:       "Display name",
    input_video: "static/videos/<id>_input.mp4",  // or null
    turntable:   null,                            // or a path to a pre-rendered mp4
    num_frames:  16,                              // 16 or 32
    axis_up:     "y"                              // 'y', 'z', or 'x'
}
```

- When `turntable` is `null`, the viewer loads `static/meshes/<id>/frame_XXXX.ply`
  on demand and the slider scrubs through time.
- When `turntable` points to an mp4, that video plays in place of the
  interactive viewer (useful for long sequences or very heavy meshes).

## Citation

```
@inproceedings{sculpt4d2026,
  title={Sculpt4D: Generating 4D Shapes via Sparse-Attention Diffusion Transformers},
  author={Yin, Minghao and Hu, Wenbo and Xu, Jiale and Shan, Ying and Han, Kai},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2026}
}
```

## Acknowledgements

Website template inspired by [Nerfies](https://nerfies.github.io/).
