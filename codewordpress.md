# ZCODESTART VÀ QUERY TAXONOMY
	$items = cs_get_option('tour_category');
	foreach ($items as $item) {
		global $cat_id;
		echo $cat_id = $item['tour_item'];
	}

	$terms = get_terms( 'danh-muc-tour' ); 
	$term_ids = wp_list_pluck( $terms, 'term_id' );

	// proceed with tax query
	$args = array ('tax_query' => array(
	    array(
	        'taxonomy' => 'danh-muc-tour',
	        'field' => 'term_id',
	        'terms' =>  $cat_id//$term_ids,
	    )
	)
	);
