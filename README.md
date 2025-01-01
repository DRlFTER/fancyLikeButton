# Fancy Like Button

## Overview
The **Fancy Like Button** is a React component that provides an interactive and visually engaging "like" button experience. Built with **Framer Motion** for smooth animations and **React** state management, this button adds floating hearts and expanding circles as dynamic feedback when clicked. This component is perfect for applications requiring an aesthetically pleasing and fun user interaction.

## Features
- **Animated Hearts:** Floating heart animations triggered upon button click.
- **Expanding Circles:** Rings of circles that expand and fade out to enhance the visual effect.
- **Customizable Animation:** Built using Framer Motion, allowing easy adjustment of animation properties.
- **Responsive Design:** Fully responsive and optimized for different screen sizes.

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

