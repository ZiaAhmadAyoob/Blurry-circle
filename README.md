# Blurry-circle

```python
let blockerVisible = true;
const blocker = document.createElement("div");

// Main blocker style
blocker.style.position = "fixed";
blocker.style.bottom = "60px";
blocker.style.right = "25px";
blocker.style.width = "180px";
blocker.style.height = "180px";
blocker.style.backdropFilter = "blur(20px)";
blocker.style.backgroundColor = "rgba(0,0,0,0.3)";
blocker.style.borderRadius = "50%";
blocker.style.zIndex = "9999";
blocker.style.cursor = "move";
blocker.style.userSelect = "none";
blocker.style.resize = "both";
blocker.style.overflow = "hidden";
document.body.appendChild(blocker);

// Toggle visibility with 'H'
document.addEventListener("keydown", function(e) {
  if (e.key.toLowerCase() === "h") {
    blockerVisible = !blockerVisible;
    blocker.style.display = blockerVisible ? "block" : "none";
  }
});

// Make blocker draggable
let isDragging = false;
let offsetX, offsetY;

blocker.addEventListener("mousedown", (e) => {
  // Avoid dragging when resizing
  if (e.offsetX > blocker.clientWidth - 20 && e.offsetY > blocker.clientHeight - 20) return;

  isDragging = true;
  offsetX = e.clientX - blocker.getBoundingClientRect().left;
  offsetY = e.clientY - blocker.getBoundingClientRect().top;
});

document.addEventListener("mousemove", (e) => {
  if (isDragging) {
    blocker.style.left = `${e.clientX - offsetX}px`;
    blocker.style.top = `${e.clientY - offsetY}px`;
    blocker.style.right = "auto";
    blocker.style.bottom = "auto";
  }
});

document.addEventListener("mouseup", () => {
  isDragging = false;
});


```
