<script lang="ts">
	import { gsap } from 'gsap';
	import ScrollTrigger from 'gsap/ScrollTrigger';
	import { TextPlugin } from 'gsap/TextPlugin';
	import { onMount } from 'svelte';
	import arrowDown from '$lib/assets/arrow-down.svg';
	import svelteLogo from '$lib/assets/svelte-logo.svg';
	import tailwindLogo from '$lib/assets/tailwindcss-logo.svg';

	gsap.registerPlugin(ScrollTrigger);
	gsap.registerPlugin(TextPlugin);

	onMount(() => {
		const svh = document.getElementById('container')!.getBoundingClientRect().height / 100;
		const svw = document.getElementById('container')!.getBoundingClientRect().width / 100;

		// gsap.to('#main-heading', {
		//  y: () => -10 * svh,
		//  delay: 1,
		//  scale: 1.1,
		//  duration: 1.2
		// });
		// gsap.to('.scroll-text', {
		//  opacity: 1,
		//  delay: 1,
		//  scale: 1.1,
		//  duration: 1.2
		// });

		gsap.to('.line', {
			height: () => 100 * svh,
			duration: 1.5
		});

		gsap.to('#main-heading', {
			y: () => -30 * svh,
			scale: 0.9,
			scrollTrigger: {
				start: 'top top',
				end: () => `top+=${100 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});
		gsap.to('.scroll-text', {
			opacity: 0,
			scale: 0.9,
			scrollTrigger: {
				start: 'top top',
				end: () => `top+=${100 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});
		gsap.to('.main-text', {
			opacity: 1,
			scale: 1.1,
			scrollTrigger: {
				start: 'top top',
				end: () => `top+=${100 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});

		gsap.to('#main-heading', {
			// opacity: 0,
			text: {
				value: 'My Favorite Tech Stack'
			},
			scrollTrigger: {
				start: () => `top+=${100 * svh} top`,
				end: () => `top+=${200 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});
		gsap.to('.main-text', {
			// opacity: 0,
			text: {
				value:
					'I mainly use Svelte. Why Svelte? Because I love how simple it is—each file is just one component. It makes everything super neat.'
			},
			width: () => 30 * svw,
			scrollTrigger: {
				start: () => `top+=${100 * svh} top`,
				end: () => `top+=${200 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});
		gsap.to('.main-text', {
			// opacity: 0,
			text: {
				value:
					'Next up is Tailwind CSS. It’s a utility-first CSS framework that’s just so simple to use and has tons of uses.'
			},
			scrollTrigger: {
				start: () => `top+=${200 * svh} top`,
				end: () => `top+=${300 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});

		gsap.to('.svelte-logo', {
			opacity: 1,
			scale: 1.1,
			scrollTrigger: {
				start: () => `top+=${100 * svh} top`,
				end: () => `top+=${200 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});
		gsap.to('.svelte-logo', {
			opacity: 0,
			scrollTrigger: {
				start: () => `top+=${200 * svh} top`,
				end: () => `top+=${300 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});

		gsap.to('.tailwind-logo', {
			opacity: 1,
			scale: 1.1,
			scrollTrigger: {
				start: () => `top+=${200 * svh} top`,
				end: () => `top+=${300 * svh} top`,
				scrub: true,
				trigger: '#scroll-container'
			}
		});

		gsap.utils.toArray('#social-media-list > .social-media').forEach((item: any) => {
			const anim = gsap.fromTo(
				item,
				{
					backgroundColor: 'oklch(100% 0 0)',
					color: 'oklch(0% 0 0)'
				},
				{
					backgroundColor: 'oklch(70.5% 0.213 47.604)',
					color: 'oklch(100% 0 0)',
					scale: 1.03,
					paused: true,
					duration: 0.3
				}
			);

			item.addEventListener('mouseenter', () => anim.play());
			item.addEventListener('mouseleave', () => anim.reverse());
		});

		gsap.utils.toArray('#projects-list > .project').forEach((project: any) => {
			const anim = gsap.to(project, {
				scale: 1.05,
				paused: true,
				duration: 0.3
			});

			project.addEventListener('mouseenter', () => anim.play());
			project.addEventListener('mouseleave', () => anim.reverse());
		});
	});
</script>

<div id="scroll-container" class="relative h-[400svh] w-[100svw]">
	<div class="absolute top-0 h-[100svh] w-[100svw] snap-start"></div>
	<div class="absolute top-[100svh] h-[100svh] w-[100svw] snap-start"></div>
	<div class="absolute top-[200svh] h-[100svh] w-[100svw] snap-start"></div>
	<div class="absolute top-[300svh] h-[100svh] w-[100svw] snap-start"></div>
	<div class="sticky top-0 h-[100svh] w-[100svw]">
		<div id="container" class="relative h-[100svh] w-[100svw]">
			<div class="line absolute top-0 left-[6lvh] h-0 w-[2lvh] bg-orange-500"></div>
			<div class="line absolute right-[6lvh] bottom-0 h-0 w-[2lvh] bg-orange-500"></div>
			<h1
				class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-[15lvh] text-center text-[6lvh]"
				id="main-heading"
			>
				Hey there! I'm <span class="kaushan text-orange-500">Loselen</span>
			</h1>
			<p class="scroll-text absolute top-1/2 left-1/2 -translate-x-1/2 text-[3lvh]">Scroll Down</p>
			<img
				src={arrowDown}
				alt="Arrow down"
				class="scroll-text absolute top-1/2 left-1/2 h-[5lvh] -translate-x-1/2 translate-y-[5lvh]"
			/>
			<p
				class="main-text poppins absolute top-[40lvh] left-[20svw] w-[60svw] text-[3lvh] leading-[5lvh] opacity-0"
			>
				I'm a super-curious person who loves to experiment with anything new and interesting, like: <br
				/> <br />
				Web Development<br />
				Game Development<br />
				Making Music<br />
				Pixel Art<br />
				Graphic Design<br />
			</p>

			<img
				src={svelteLogo}
				alt="Svelte logo"
				class="svelte-logo absolute top-[28lvh] left-[58svw] w-[28svw] opacity-0"
			/>
			<img
				src={tailwindLogo}
				alt="Tailwind logo"
				class="tailwind-logo absolute top-[50lvh] left-[58svw] w-[28svw] opacity-0"
			/>
		</div>
	</div>
</div>

<div class="relative h-[200svh] w-[100svw] snap-start">
	<div class="absolute top-0 left-[6lvh] h-full w-[2lvh] bg-orange-500"></div>
	<div class="absolute right-[6lvh] bottom-0 h-full w-[2lvh] bg-orange-500"></div>
	<h2 class="absolute top-[10lvh] left-1/2 -translate-x-1/2 text-center text-[5lvh]">
		<span class="kaushan text-orange-500">Selected</span> Projects
	</h2>
	<div id="projects-list">
		<div
			class="project absolute top-[25lvh] left-1/2 h-[40lvh] w-[70svw] -translate-x-1/2 shadow-2xl"
		>
			<div class="relative h-full w-full">
				<h3
					class="kaushan absolute top-0 left-0 -translate-[3lvh] -rotate-[6deg] text-[4lvh] text-orange-500 text-shadow-lg/10 text-shadow-black"
				>
					Cherry Blossom
				</h3>
				<p
					class="poppins absolute top-[5lvh] left-[2lvh] w-[calc(70svw-50lvh)] text-[2lvh] leading-[3.5lvh]"
				>
					Cherry Blossom ID is an importer and exporter of traditional musical instruments based in
					Blitar. They conduct international trade of various traditional instruments, primarily
					exporting to countries like China. The website is accessible here: <a
						href="https://cherryblossom.id"
						class="text-orange-500 underline">cherryblossom.id</a
					>
				</p>
				<p class="absolute bottom-[2lvh] left-[2lvh] text-[2lvh] text-orange-500">#ClientProject</p>
				<div
					class="absolute top-1/2 right-[4lvh] aspect-4/3 h-[calc(100%-10lvh)] -translate-y-1/2 border-[0.4lvh] border-orange-500"
				></div>
			</div>
		</div>
		<div
			class="project absolute top-[70lvh] left-1/2 h-[40lvh] w-[70svw] -translate-x-1/2 shadow-2xl"
		>
			<div class="relative h-full w-full">
				<h3
					class="kaushan absolute top-0 left-0 -translate-[3lvh] -rotate-[6deg] text-[4lvh] text-orange-500 text-shadow-lg/10 text-shadow-black"
				>
					Simple To Do App
				</h3>
				<p
					class="poppins absolute top-[5lvh] left-[2lvh] w-[calc(70svw-50lvh)] text-[2lvh] leading-[3.5lvh]"
				>
					This is a straightforward to-do list application project. It served as a learning exercise
					focused on implementing state management and fundamental CRUD (Create, Read, Update,
					Delete) operations.
				</p>
				<p class="absolute bottom-[2lvh] left-[2lvh] text-[2lvh] text-orange-500">
					#PersonalProject
				</p>
				<div
					class="absolute top-1/2 right-[4lvh] aspect-4/3 h-[calc(100%-10lvh)] -translate-y-1/2 border-[0.4lvh] border-orange-500"
				></div>
			</div>
		</div>
	</div>
</div>

<div class="relative h-[100svh] w-[100svw] snap-start">
	<div class="absolute top-0 left-[6lvh] h-full w-[2lvh] bg-orange-500"></div>
	<div class="absolute right-[6lvh] bottom-0 h-full w-[2lvh] bg-orange-500"></div>
	<h2 class="absolute top-[5lvh] left-1/2 -translate-x-1/2 text-[5lvh]" id="about-me">
		<span class="kaushan text-orange-500">Loselen's</span> Hangout Spots
	</h2>
	<div id="social-media-list">
		<div
			class="social-media absolute top-[30lvh] left-[20svw] h-[9lvh] w-[60svw] border-[0.37lvh] border-orange-500"
		>
			<div class="relative h-full w-full">
				<div class="absolute top-[3.5lvh] left-[2lvh] h-[1lvh] w-[3lvh] bg-orange-500"></div>
				<div class="absolute top-[2.5lvh] left-[3lvh] h-[3lvh] w-[1lvh] bg-orange-500"></div>
				<p class="absolute top-1/2 left-[8lvh] -translate-y-1/2 text-[3lvh]">
					GitHub: loselen-lu (Code stuff)
				</p>
			</div>
		</div>
		<div
			class="social-media absolute top-[42lvh] left-[20svw] h-[9lvh] w-[60svw] border-[0.37lvh] border-orange-500"
		>
			<div class="relative h-full w-full">
				<div class="absolute top-[3.5lvh] left-[2lvh] h-[1lvh] w-[3lvh] bg-orange-500"></div>
				<div class="absolute top-[2.5lvh] left-[3lvh] h-[3lvh] w-[1lvh] bg-orange-500"></div>
				<p class="absolute top-1/2 left-[8lvh] -translate-y-1/2 text-[3lvh]">
					Instagram: loselen.luari (My art/life)
				</p>
			</div>
		</div>
		<div
			class="social-media absolute top-[54lvh] left-[20svw] h-[9lvh] w-[60svw] border-[0.37lvh] border-orange-500"
		>
			<div class="relative h-full w-full">
				<div class="absolute top-[3.5lvh] left-[2lvh] h-[1lvh] w-[3lvh] bg-orange-500"></div>
				<div class="absolute top-[2.5lvh] left-[3lvh] h-[3lvh] w-[1lvh] bg-orange-500"></div>
				<p class="absolute top-1/2 left-[8lvh] -translate-y-1/2 text-[3lvh]">
					Pinterest: loselenluari (Inspiration)
				</p>
			</div>
		</div>
		<div
			class="social-media absolute top-[66lvh] left-[20svw] h-[9lvh] w-[60svw] border-[0.37lvh] border-orange-500"
		>
			<div class="relative h-full w-full">
				<div class="absolute top-[3.5lvh] left-[2lvh] h-[1lvh] w-[3lvh] bg-orange-500"></div>
				<div class="absolute top-[2.5lvh] left-[3lvh] h-[3lvh] w-[1lvh] bg-orange-500"></div>
				<p class="absolute top-1/2 left-[8lvh] -translate-y-1/2 text-[3lvh]">
					Email: keranairhujan1234@gmail.com (Say hi!)
				</p>
			</div>
		</div>
	</div>
</div>
