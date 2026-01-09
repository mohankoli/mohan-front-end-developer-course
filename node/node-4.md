- **Difference between `fs.readFile` and `fs.createReadStream`**

| Feature            | `fs.readFile`                     | `fs.createReadStream`              |
|--------------------|----------------------------------|------------------------------------|
| Data Reading       | Reads entire file at once         | Reads file in chunks               |
| Memory Usage       | High (loads full file in memory)  | Low (memory efficient)             |
| Speed (Large Files)| Slower                            | Faster                              |
| Suitable For       | Small files                       | Large files                         |
| Type               | Asynchronous function             | Stream-based approach               |
