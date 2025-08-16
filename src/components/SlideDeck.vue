<template>
	<div class="slide-deck" @keydown="handleKeydown" tabindex="0">
		<!-- Slide Header -->
		<div class="slide-header">
			<div class="header-content">
				<div class="avatar-container">
					<img src="/jon.svg" alt="Jon Ellwood" class="avatar" />
				</div>
				<h1>Customer Relationships</h1>
				<div class="slide-counter">
					{{ currentSlide + 1 }} / {{ slides.length }}
				</div>
			</div>
		</div>
		<!-- Slides -->
		<component
			:is="slides[currentSlide].component"
			:class="['slide', { active: true }]"
			:key="currentSlide" />

		<!-- Navigation Hint -->
		<div class="nav-hint">Use ← → or Space to navigate</div>

		<!-- Footer -->
		<div class="slide-footer">
			Customer Relationships: For the People We Serve
		</div>
	</div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import TitleSlide from './slides/TitleSlide.vue';
import OpeningSlide from './slides/OpeningSlide.vue';
import CoreConceptSlide from './slides/CoreConceptSlide.vue';
import BasicAutoCompleteSlide from './slides/BasicAutoCompleteSlide.vue';
import ContextualDataSlide from './slides/ContextualDataSlide.vue';
import PredictiveDataSlide from './slides/PredictiveDataSlide.vue';
import TechnicalConsiderationsSlide from './slides/TechnicalConsiderationsSlide.vue';
import ROISlide from './slides/ROISlide.vue';
import ClosingSlide from './slides/ClosingSlide.vue';

const currentSlide = ref(0);

// Speaker Notes:
// - Use View Transitions API for smooth slide changes
// - Each slide has animated bullet reveals
// - Keyboard navigation: left/right arrows or spacebar to advance
// - This follows the talk outline structure from talk_outline.md

const slides = [
	{ component: TitleSlide, duration: '30s' },
	{ component: OpeningSlide, duration: '3min' },
	{ component: CoreConceptSlide, duration: '5min' },
	{ component: BasicAutoCompleteSlide, duration: '2-3min' },
	{ component: ContextualDataSlide, duration: '3min' },
	{ component: PredictiveDataSlide, duration: '2-3min' },
	{ component: TechnicalConsiderationsSlide, duration: '2min' },
	{ component: ROISlide, duration: '1min' },
	{ component: ClosingSlide, duration: '1min' },
];

const nextSlide = () => {
	if (currentSlide.value < slides.length - 1) {
		currentSlide.value++;
	}
};

const prevSlide = () => {
	if (currentSlide.value > 0) {
		currentSlide.value--;
	}
};

const handleKeydown = (event) => {
	switch (event.key) {
		case 'ArrowRight':
		case ' ':
		case 'PageDown':
			event.preventDefault();
			nextSlide();
			break;
		case 'ArrowLeft':
		case 'PageUp':
			event.preventDefault();
			prevSlide();
			break;
		case 'Home':
			event.preventDefault();
			currentSlide.value = 0;
			break;
		case 'End':
			event.preventDefault();
			currentSlide.value = slides.length - 1;
			break;
	}
};

onMounted(() => {
	// Focus the deck for keyboard events
	document.querySelector('.slide-deck').focus();
});

onUnmounted(() => {
	// Cleanup if needed
});
</script>

<style scoped>
.slide-deck:focus {
	outline: none;
}
</style>
