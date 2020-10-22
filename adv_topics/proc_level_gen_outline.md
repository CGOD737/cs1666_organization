# Procedural Level Generation Advanced Topic Presentations

## Presentation I (Oct. 7):
* What is Procedural Generation?
	* Used to create “unique” worlds, levels, loot, encounters
	* Different than Random Generation
	* Commonly uses Noise
* History and Examples
	* Early Use in Gaming\
		* Akalabeth and Rogue
		* Diablo and Daggerfall
	* Graphics / Animation
	* Open World - Worlds
		* Dwarf Fortress
		* Minecraft
		* No Man’s Sky
	* Action - Loot
		* Borderlands
* How does it work?
	* Basics
		* Perlin Noise
	* Algorithms
		* Diamond Square
		* Spelunky Case Study
* Why use Procedural Generation?
	* Pros
		* Smaller file sizes
		* Generate large amounts of content
		* Extra time available for complex gameplay
		* Higher replayability
		* Adjustable Difficulty
	* Cons
		* Complexity of implementation
		* Risk of creating predictable content
		* Loss of Fine Tuned Control
* Applying it to our game
	* Procedurally generated sections connecting premade zones
	* Generate traversable, fun environments appropriate for current loadout
	* Challenge: procedurally generated areas must always have a path that players can traverse with their current gear

## Presentation II (Oct. 21):
# What is Binary Space Partitioning?
* Method for recursively subdividing a space into two convex sets
* History of Binary Space Partitioning
# How does it work?
* Creating the binary tree
* Drawing the rectangles in each leaf node
* Connecting the rectangles with hallways
# What games use BSP?
* Doom (1993)
* Quake (1996)
# Pros
* Good for collision detection and handling
* Easy to visualize with tiles/arrays
* Produces noticeable randomness each time
# Cons
* Generating a BSP tree can be time-consuming/resource intensive
* Can get rather complicated to implement
# How did we implement it?
* Variable parameters
  * Room size
  * Map size
  * Hallway size
  * Tile size
Array integration
SDL_Surface/Rect Usage


## Presentation III (Nov. 2):

* Strategy
	* Terrain generation is hard.
	* Create basic terrain for physics and networking team to work with
	* Start developing the tools we need…
* XorShift - fast seeded RNG
* Simplex Noise
	* The difference between perlin and simplex
	* Advantages of simplex
	* Higher dimensional noise with simplex
* Simplex Worms/Perlin Worms
	* Slight twist! We need more control over our random worm’s directions
	* We solve by using the simplex values as accelerations and not the velocities
	* How to voxelize worm path into a thicc cave?
		* Distance from point-to-line equation
			* Get closest line to the point
			* Do point to line equation
			* Set voxel density accordingly (mess with constants)
		* Circle cut-out
			* Cut a gradient circle out of each point in the path
		* Advantages/Disadvantages
			* Point-to-line is faster
			* For circle cut-out points need to be tightly packed
			* Circle cut-out has easier implementation, especially with varying cave width
* Marching Squares
	* What is it
		* Iterate cases
		* The lookup tables
		* Slight twist! Optimize for ambiguity between directions
	* Our implementation
		* Just fill squares at the cases of all on and all off.
		* Use different rendering code for each individual case
		* Simplify the case down into its triangles and its rectangles.
		* Render rectangles
		* Render triangles with a slope based line by line scanning algorithm (1px by n-px SDL lines)
* Non-procedural terrain injection
	* Easy creation (parse .bmp files)
	* Parse all of them at game start time
	* Name them by indexable pattern
	* Define possible entry points (all will need a top/bottom/left/right)
	* Add post-processing--on injection--to blend the edges with procedural terrain
* Entity Spawning and Path Generation
	* Spawn by raycast down from simplex worm points
		* Prevents spawning on cave walls or outside of cave
		* Its fast
	* Enemy paths
		* For walking enemies they need flat terrain
		* Choose a direction and walk
		* Turn around if too steep


## Presentation IV (Nov. 16):
* 

