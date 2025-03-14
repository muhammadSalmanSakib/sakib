<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Portfolio - Salman Hossain Sakib</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #0a0a0a;
            color: white;
            text-align: center;
        }
        canvas {
            display: block;
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
        }
        .container {
            position: relative;
            z-index: 1;
            padding: 50px;
        }
        h1 {
            font-size: 3em;
        }
        p {
            font-size: 1.5em;
        }
    </style>
    <!-- Head section updated -->
</head>
<body>
    <canvas id="bg"></canvas>
    <div class="container">
        <h1>Salman Hossain Sakib</h1>
        <p>SEO Expert | Digital Marketer | Photographer</p>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // Initialize Three.js Scene
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ canvas: document.getElementById("bg"), alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(window.devicePixelRatio);

        // Create a 3D Torus Knot
        const geometry = new THREE.TorusKnotGeometry(10, 3, 100, 16);
        const material = new THREE.MeshStandardMaterial({ color: 0xff6600, wireframe: true });
        const torusKnot = new THREE.Mesh(geometry, material);
        scene.add(torusKnot);

        // Lighting
        const light = new THREE.PointLight(0xffffff, 1, 100);
        light.position.set(20, 20, 20);
        scene.add(light);

        // Camera position
        camera.position.z = 50;

        // Animation loop
        function animate() {
            torusKnot.rotation.x += 0.01;
            torusKnot.rotation.y += 0.01;
            renderer.render(scene, camera);
            setTimeout(() => {
                animate();
            }, 16); // Equivalent to ~60FPS
        }
        animate();

        // Handle screen resize
        window.addEventListener('resize', () => {
            renderer.setSize(window.innerWidth, window.innerHeight);
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
        });
    </script>
</body>
</html>
