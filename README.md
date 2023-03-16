# Junior To Senior Developer Roadmap

## 1. SSH (Secure Shell):

SSH (Secure Shell) is a network protocol that allows secure remote access to a computer or server over an unsecured network. It provides a secure channel for remote communication between two computers, using encryption to protect data exchanged over the network.
<br/>
SSH is widely used for remote login and file transfer between machines running different operating systems, including Linux, macOS, and Windows. It provides a way to securely access a remote computer, execute commands, and transfer files over the network.

To access a remote laptop through SSH: `ssh {user}@{host}`

### Symmetrical Encryption

Symmetric encryption, also known as secret key encryption, is a type of encryption where the same secret key is used for both encryption and decryption of a message. In other words, the sender and receiver of the message share a secret key that is used to transform plaintext into ciphertext and vice versa.
<br>
In symmetric encryption, the encryption algorithm uses a key to scramble the plaintext into ciphertext. The same key is then used by the decryption algorithm to unscramble the ciphertext back into plaintext. Since the same key is used for both encryption and decryption, the key must be kept secret to ensure the security of the message.
<br>
The security of symmetric encryption depends on the strength of the key used. If the key is too weak, an attacker may be able to easily guess the key or use brute force methods to try many possible keys until the correct one is found. Therefore, it is important to use strong and random keys to ensure the security of the message.

### Asymmetrical Encryption

Asymmetric encryption, also known as public key encryption, is a type of encryption that uses two different but mathematically related keys for encryption and decryption of a message. One key is known as the public key and is used for encryption, while the other key is known as the private key and is used for decryption.
<br>
In asymmetric encryption, the public key can be freely distributed to anyone who wants to send a message to the owner of the private key. The sender uses the recipient's public key to encrypt the message, which can only be decrypted by the recipient using their private key. This means that the sender and recipient do not need to share a secret key beforehand, as is the case with symmetric encryption.

### Hashing

Hashing is the process of converting any input data (such as a message, file, or password) into a fixed-size output known as a hash. A hash function takes the input data and generates a hash value that is unique to that input data.
<br>
Hashing has several important properties, including:

1. Deterministic: For a given input, the hash function will always produce the same output.
2. Fixed-size: The output hash value has a fixed length, regardless of the size of the input.
3. One-way: It is computationally infeasible to determine the input data from the hash value.
4. Collision-resistant: It is difficult to find two different inputs that produce the same hash value.

<br>

When an SSH client connects to an SSH server for the first time, the server sends its public key to the client for verification. The client can then use a hash function to generate a hash of the server's public key and compare it to a known value, which is stored on the client's system. This process helps to ensure that the client is communicating with the correct server and not an imposter.

## Performance

1. Minimize Text: <br>
   Use webpack to build the website aka minimizing the sizes of HTML, CSS and JS files.

2. Minmize Images: <br>
   JPG (or JPEG): It is a lossy image compression format that reduces the size of the image file by discarding some of the image data. It is widely used for photographs, as it can compress the image file size significantly without significant loss of image quality. JPG images are commonly used on the web.
   <br>
   PNG: It is a lossless image compression format that preserves all the image data. It supports transparency and is best suited for images with text, graphics, or logos with a transparent background. PNG images are commonly used for web graphics, logos, and icons.
   <br>
   SVG: It is a vector graphics format that is scalable and can be resized without loss of quality. SVG images are made up of mathematical equations and are best suited for logos, icons, and other graphics that need to be scaled to different sizes. They are commonly used on the web and in print media.
   <br>
   GIF: It is a lossless image compression format that supports animation. GIF images are commonly used for short animations, logos, and icons. They support up to 256 colors, which makes them best suited for simple images with few colors.
   <br>

In summary, JPG is best for photographs, PNG is best for images with text or logos that need transparency, SVG is best for scalable vector graphics, and GIF is best for short animations, logos, and icons.

3. Optimize Image Delivery: <br>

- use media queries to deliver different image backgrounds for different screens sizes.
- Use `imigix` that uses CDNs
- Remove photos metadata

4. Critical Render Path: <br>
   The critical render path in web development refers to the sequence of steps that a web browser follows to receive, parse, and render the content of a web page. It includes all the actions that need to take place before a user can see and interact with the page.

The critical render path involves the following steps: <br>

1. Retrieving HTML, CSS, and JavaScript files from the server
2. Parsing HTML to create the Document Object Model (DOM)
3. Parsing CSS to create the CSS Object Model (CSSOM)
4. Combining the DOM and CSSOM to create the render tree
5. Laying out the render tree to determine the position and size of each element
6. Painting the pixels onto the screen <br>

The critical render path is called "critical" because it determines how quickly a page can be loaded and displayed to the user. Optimizing the critical render path can improve page load times, which can lead to better user engagement and higher conversion rates.
<br>

- Load `<script>` tags after the `<body>` tag because JS waits for HTML and CSS to finish being parsed to create the render tree.
- Internal CSS Pro: Allows us to not have to request CSS file. Use it for critical CSS.
- CSS is render blocking so use these techniques:
  - Load only what is needed
  - Above the fold loading:
  ```
   <script>
      // Load the rest of the CSS asynchronously
      var link = document.createElement('link');
      link.rel = 'stylesheet';
      link.href = 'style3.css';
      document.head.appendChild(link);
   </script>
  ```
  - Media attributes
  - Less specifity
- Adding the `defer` attribute to a `script` tag tells the browser to download the script file while the rest of the page continues to load, but defer execution of the script until the page has finished loading. This means that the script will be executed in the order it appears in the HTML file, and after the page has finished loading.
- The `async` attribute tells the browser to download the script file while the rest of the page continues to load, and then execute the script as soon as it's downloaded, regardless of whether the rest of the page has finished loading. This means that the script can execute out of order with respect to the rest of the page, potentially causing unexpected behavior.

### HTTP vs HTTP/2

HTTP (Hypertext Transfer Protocol) and HTTP/2 are both protocols for transferring data over the internet. However, there are several key differences between the two:

- Speed: HTTP/2 is faster than HTTP. HTTP/2 uses a new binary format that compresses headers, reducing the amount of data that needs to be sent. Additionally, HTTP/2 allows multiple requests to be sent over a single connection, which reduces the latency of the connection.

- Multiplexing: HTTP/2 supports multiplexing, which allows multiple requests to be sent over a single connection simultaneously. This is in contrast to HTTP, where each request requires a separate connection.

- Server push: HTTP/2 supports server push, which allows the server to send data to the client without waiting for a request. This can improve performance by allowing the server to send data that the client is likely to request in the future.

- Security: While both protocols support encryption, HTTP/2 requires the use of encryption. This helps to protect against eavesdropping and other types of attacks.
