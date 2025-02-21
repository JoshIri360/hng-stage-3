# 3D Avatar Interaction Mobile App  
*A React Native + Three.js Adventure*  

---

## 📱 Overview  
This project is my journey into mobile 3D development during the HNG Internship. Built with React Native, React Three Fiber, and TypeScript, it features two interactive Ready Player Me avatars that respond to touch controls, perform animations, and "communicate" (read: awkwardly face each other).  

**Key Features:**  
- Load and render two 3D models (.glb)  
- Mobile touch controls for movement/direction  
- Animation states (idle, talk, dance, fall)  
- Dynamic texture mapping and shadows  
- Hot-swappable avatar models  

---

## 🛠️ Installation  
1. Clone the repo:  
   ```bash  
   git clone https://github.com/JoshIri360/hng-stage-3.git  
   ```  
2. Install dependencies:  
   ```bash  
   npm install # or yarn install  
   ```  
3. Run on Android (emulator/physical device):  
   ```bash  
   npx react-native run-android  
   ```  

**⚠️ Note:** iOS builds currently fail due to unresolved GLTF loader issues. [See "Known Issues" below](#-known-issues).  

---

## 🎮 Usage  
- **Movement:** On-screen directional buttons to rotate/move avatars  
- **Animations:** Toggle between idle, talk, dance, and fall states  
- **Reset:** Return avatars to default positions  
- **Model Swapping:** Load custom .glb files via URL  

---

## 💡 Technical Highlights  
1. **Rotation Logic:**  
   ```typescript  
   // Converts direction to Euler angles  
   const getRotationForDirection = (direction: Direction) => {  
     switch(direction) {  
       case 'left': return [0, -Math.PI/2, 0];  
       // ...  
     }  
   };  
   ```  
   [See full implementation](/src/App.tsx#L24-L36)  

2. **Shared Material System:**  
   Reuses texture maps across avatars to optimize memory:  
   ```typescript  
   const [texture, normalMap] = useTexture([...]);  
   ```  

3. **State-Driven Animation:**  
   ```typescript  
   <Avatar  
     modelPath={maleState.modelPath}  
     state={maleState} // Controls position/rotation/anim  
   />  
   ```  

---

## 🚧 Known Issues  
- **iOS Builds:** Fails due to `@react-three/drei/native` compatibility  
- **Performance:** Framerate drops on low-end Android devices  
- **Texture Loading:** Occasional crashes with large .jpg files  

---

## 📚 Learn More  
For the full story (including my battles with Unity, Blender, and Xcode):  
🔗 **[Building a 3D Avatar App: My Third Task at HNG Internship](https://medium.com/@aidelojejoshua/building-a-3d-avatar-app-my-third-task-at-hng-internship-95bfb2cf563d)**  

---

## 🙏 Acknowledgments  
- 3D Assets: [Ready Player Me](https://readyplayer.me)  
- Libraries: [React Three Fiber](https://docs.pmnd.rs), [Drei](https://github.com/pmndrs/drei)  
- Internship: [HNG](https://hng.tech)  

---

**Built with:**  
[![React Native](https://img.shields.io/badge/React_Native-20232A?style=flat&logo=react)](https://reactnative.dev)  
[![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat&logo=three.js)](https://threejs.org)  
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript)](https://www.typescriptlang.org/)  
