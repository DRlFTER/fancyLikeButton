# Fancy Like Button

## Overview
The **Fancy Like Button** is a React component that provides an interactive and visually engaging "like" button experience. Built with **Framer Motion** for smooth animations and **React** state management, this button adds floating hearts and expanding circles as dynamic feedback when clicked. This component is perfect for applications requiring an aesthetically pleasing and fun user interaction.

## Code
Here's the jsx code of the component so you don't have to download any files
```bash
import { motion } from "framer-motion";
import { useState } from "react";

export const FancyLikeButton = () => {
  const [hearts, setHearts] = useState([]);
  const [circles, setCircles] = useState([]);

  const handleButtonClick = () => {
    const xNum = Math.floor(Math.random() * 150) - 75;

    const newHeart = {
      id: Date.now(),
      xHeart: xNum,
    };

    const newCircles = Array.from({ length: 15 }, (_, i) => ({
      id: Date.now() + i,
      delay: i * 0.015,
      size: 16 - i,
      xCircle: xNum,
    }));

    setCircles((prevCircles) => [...prevCircles, ...newCircles]);
    setHearts((prevHearts) => [...prevHearts, newHeart]);

    setTimeout(() => {
      setHearts((prevHearts) =>
        prevHearts.filter((heart) => heart.id !== newHeart.id)
      );
      setCircles((prevCircles) =>
        prevCircles.filter((circle) => circle.id !== newCircles.id)
      );
    }, 2000);
  };

  return (
    <div className="flex flex-col flex-1 w-1/3">
      <div className="my-2 py-3 px-5 rounded-3xl flex justify-center items-center bg-[#606B75]">
        <h3 className="text-third-title flex-1 pl-5 text-[#1B2224] font-semibold font-mono">
          Fancy like button
        </h3>
      </div>
      <div className="h-96 my-2 rounded-2xl bg-[#505C67] flex flex-col items-center justify-center overflow-hidden p-5">
        <div className="flex flex-col w-full h-full rounded-xl p-3 pt-20 gap-3 justify-center items-center">
          <div className="relative flex">
            <motion.button
              className="h-20 w-20 bg-[#2C3A47] rounded-full flex justify-center items-center z-30"
              onTap={handleButtonClick}
              initial={{ scale: 1.1 }}
              whileTap={{ scale: 0.9 }}
              transition={{ type: "spring", stiffness: 400, duration: 0.3 }}
            >
              <svg
                version="1.1"
                id="Layer_1"
                xmlns="http://www.w3.org/2000/svg"
                x="0px"
                y="-10px"
                width="40.44px"
                height="53.71px"
                viewBox="0 0 122.88 107.41"
                style={{ enableBackground: "new 0 0 122.88 107.41" }}
                className="pt-1"
              >
                <style type="text/css">
                  {`.st0{fill-rule:evenodd;clip-rule:evenodd;}`}
                </style>
                <g>
                  <path
                    className="st0"
                    d="M60.83,17.19C68.84,8.84,74.45,1.62,86.79,0.21c23.17-2.66,44.48,21.06,32.78,44.41 c-3.33,6.65-10.11,14.56-17.61,22.32c-8.23,8.52-17.34,16.87-23.72,23.2l-17.4,17.26L46.46,93.56C29.16,76.9,0.95,55.93,0.02,29.95 C-0.63,11.75,13.73,0.09,30.25,0.3C45.01,0.5,51.22,7.84,60.83,17.19L60.83,17.19L60.83,17.19z"
                    fill="#A5AAB1"
                  />
                </g>
              </svg>
            </motion.button>
            {hearts.map((heart) => (
              <MiniHeart key={heart.id} xNum={heart.xHeart} />
            ))}
            {circles.map((circle) => (
              <Circles
                key={circle.id}
                xNum={circle.xCircle}
                delay={circle.delay}
                size={circle.size}
              />
            ))}
          </div>
        </div>
      </div>
    </div>
  );
};

const MiniHeart = ({ xNum }) => {
  return (
    <motion.div
      className="h-11 w-11 bg-[#2C3A47] rounded-full flex justify-center items-center absolute z-20"
      initial={{ opacity: 1, x: 0, y: 0 }}
      animate={{
        x: xNum,
        y: -(xNum + 100),
        opacity: 0,
      }}
      transition={{
        x: { duration: 0.2, ease: "easeOut" },
        y: { duration: 0.6, ease: "easeInOut" },
        opacity: { delay: 0.85, duration: 0.6 },
      }}
    >
      <svg
        version="1.1"
        id="Layer_1"
        xmlns="http://www.w3.org/2000/svg"
        x="0px"
        y="-10px"
        width="20.44px"
        height="53.71px"
        viewBox="0 0 122.88 107.41"
        style={{ enableBackground: "new 0 0 122.88 107.41" }}
        className="pt-1"
      >
        <style type="text/css">
          {`.st0{fill-rule:evenodd;clip-rule:evenodd;}`}
        </style>
        <g>
          <path
            className="st0"
            d="M60.83,17.19C68.84,8.84,74.45,1.62,86.79,0.21c23.17-2.66,44.48,21.06,32.78,44.41 c-3.33,6.65-10.11,14.56-17.61,22.32c-8.23,8.52-17.34,16.87-23.72,23.2l-17.4,17.26L46.46,93.56C29.16,76.9,0.95,55.93,0.02,29.95 C-0.63,11.75,13.73,0.09,30.25,0.3C45.01,0.5,51.22,7.84,60.83,17.19L60.83,17.19L60.83,17.19z"
            fill="#A5AAB1"
          />
        </g>
      </svg>
    </motion.div>
  );
};

const Circles = ({ xNum, delay, size }) => {
  return (
    <motion.div
      className="h-11 w-11 bg-[#2C3A47] rounded-full flex justify-center items-center absolute z-10"
      initial={{ opacity: 1, x: 0, y: 0, scale: size / 15 }}
      animate={{
        x: xNum,
        y: -(xNum + 100),
        opacity: 0,
      }}
      transition={{
        x: { duration: 0.2 + delay, delay: delay, ease: "easeOut" },
        y: { duration: 0.6 + delay, delay: delay, ease: "easeInOut" },
        opacity: { delay: 0.4 + delay, duration: 0.6 },
      }}
    ></motion.div>
  );
};

```

## Features
- **Animated Hearts:** Floating heart animations triggered upon button click.
- **Trails:** An animated trail that follows the floating hearts.
- **Customizable Animation:** Built using Framer Motion, allowing easy adjustment of animation properties.

## Installation
1. Clone the repository or copy the component's code.
2. Ensure you have **React** and **Framer Motion** installed in your project. If not, install them using:
   ```bash
   npm install react framer-motion
   ```
3. Add the `FancyLikeButton` component to your project.

## Usage
1. Import the component into your React project:
   ```javascript
   import { FancyLikeButton } from './FancyLikeButton';
   ```
2. Use it in your JSX:
   ```jsx
   <FancyLikeButton />
   ```

## Code Breakdown
### Main Component
- **FancyLikeButton:** Manages the state for hearts and circles, handles button clicks, and renders the animated elements.

### Subcomponents
- **MiniHeart:** Renders individual hearts with animations for floating and fading effects.
- **Circles:** Renders individual circles that expand and fade away for a ripple-like effect.

## Styling
The component uses Tailwind CSS for styling. Ensure your project has Tailwind CSS configured. You can customize the colors, sizes, and layout by modifying the Tailwind classes in the component code.

### Example CSS Classes Used:
- Button: `h-20 w-20 bg-[#2C3A47] rounded-full`
- Heart: `h-11 w-11 bg-[#2C3A47] rounded-full`
- Circle: `h-11 w-11 bg-[#2C3A47] rounded-full`

## Dependencies
- **React:** For building the component.
- **Framer Motion:** For handling animations.
- **Tailwind CSS:** For styling (optional).

## Customization
You can customize the component as follows:
- **Animation:** Adjust the timing, easing, and effects in the Framer Motion `motion.div` and `motion.button` elements.
- **Styling:** Modify Tailwind CSS classes to change the appearance.
- **Content:** Replace the SVG with your custom icons.

## Contributing
Feel free to submit issues or pull requests to enhance the Fancy Like Button.

## License
This component is open-source and available under the MIT License.

## Demo
Add a live link or GIF showcasing the Fancy Like Button in action.

## Author
Developed by [Your Name/Username].

