## Exemple de configuration function.php

//** disable srcset**/
function disable_wp_responsive_images() {
	return 1;
}
add_filter('max_srcset_image_width', 'disable_wp_responsive_images');
