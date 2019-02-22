# hw03-environment-setpiece

Evelyn Bailey

ebail

Project: https://www.shadertoy.com/view/3sBGDd

Website: https://evelyn.pb.studio

Features

This project is inspired by a scene from the Pixar Short, Smash and Grab. 

The Background: I color the background the hill colors if the pixel's screen space coordinates fall below the curve I defined for their shape. I linearly interpolate between the brighter color and the darker color using a t value of the screen space y coordinate remapped to a square root function. In a similar fashion, the color of the sky is also linearly interpolated between the sky color and the horizon color based on the y position. The stars in the sky are placed using a simple noise function and change colors using a noise function of the sine of the time. The intensity of each star also diminishes closer to the horizon, which I achieved by linearly interpolating the light intensity based on height.

The Geometry: For the shape of the train, I created 5 evenly spaced SDF rounded boxes and used a smooth min function to blend the shapes together. The train tracks are one solid SDF box subtracted with SDF round boxes to carve out the pillars. The position of the train is animated based on time and cycles from one end of the scene to the next every 25 seconds or so. The ground is a SDF box deformed in the xyz directions by FBM of Worley noise, and the values are remapped using a cubic function to give it a smoother look. The pillars are collections of SDF boxes with the x and y coordinate of each box offset by a small random amount to create a more organic look.

The Lighting: There are five lights in the scene: one directional that establishes the light on the tracks and the bright spots on the ground; another fill light that brightens the scene and establishes the rim of light on the top of the train; and two more directional lights that establish the color of the pillars in the sky. The material on the ground is Blinn Phong, which gives the ground a shinier look, and each object in the scene incorporates specular intensity into the color.

I also implemented penumbra shadows and ambient occlusion and incorporated them into my scene. The train tracks cast shadows on the ground, and I also use ambient occlusion where the tracks meet the ground to further darken the area. There is also ambient occlusion where the train and the tracks meet, which provides a shadow on the tracks as the train moves across the screen.

Post Processing: To further accentuate the light coming from the train light, the 'reflective' surface along the pillar, and the rocks, I rendered everything to a texture and then computed a bloom effect on the image to add a 'flare' like effect on the stars and the bright surfaces. 
