# 💡 Build a lightweight docker image

For most Python apps it is often enough to simply use a `slim-buster` [image ](https://hub.docker.com/\_/python)or even an `alpine` one.&#x20;

However, sometimes you need an additional package or two that doesn't come with these images.

While you could sometimes work your way around some issues by having a file locally, or download a .deb file or so, it is not always possible. It is all too easy to end up with a messy `Dockerfile`

We can avoid many such pitfalls by starting off from a slim OS image like Alpine



The problem with alpine is that it lacks many of the core features you'd expect to find in Ubuntu and as such docker builds take forever.
