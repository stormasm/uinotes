

- Everything starts with the PictureWidget in main.rs
- see make_picture_widget

---

Lets start out with how an image gets loaded into the application.   
And look at this across all three or four different deals I am looking at.  

In Emulsion it happens here:

##### image_cache/mod.rs

```rust
/// The process of loading an image (or animation frame) consists of the following steps.
/// Note that even still images are handled as 1 frame long animations as there is
/// semantically no difference between those and this keeps the code relatively simple.
///
/// - ImageCache - Load request sent
///     - An entry representing the request is created in `ImageCache::ongoing_requests`
/// - Worker thread - Decodes an image from the byte stream into a CPU-side buffer. Send this back on a channel
///     - Decoded pixel data on channel (CPU)
/// - ImageCache - Prefetched image received from worker thread
///     - Decoded pixel data in `ImageCache::prefetched`
/// - ImageCache - Prefetched image is uploaded to a GPU texture from the CPU
///     - Pixel data is on the gpu referred to by `ImageCache::texture_cache`
///
pub struct ImageCache {
	dir: Directory,

	//current_name: OsString,
	//current_file_idx: usize,
	current_frame_idx: usize,

	remaining_capacity: isize,
	total_capacity: isize,
	curr_est_size: isize,

	pending_requests: PendingRequests,
	texture_cache: BTreeMap<u32, CachedTexture>,
	loader: ImageLoader,
}
```

---

- Do a search for *texture_cache* so you can better understand how data gets to the gpu
- See CachedTexture as well as the fn upload_to_texture
