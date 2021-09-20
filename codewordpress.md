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
	
// THÊM SHORTCODE VÀO CONTACT 7
add_filter( 'wpcf7_form_elements', 'mycustom_wpcf7_form_elements' );
 
function mycustom_wpcf7_form_elements( $form ) {
    $form = do_shortcode( $form );
 
    return $form;
}

// Code carousel slider hoạt động
<!-- SLider -->
	<?php $items = rwmb_meta('prefix_album'); ?>
				
<div class="container mt-5">
<div class="carousel-container row">
  
<!-- Sorry! Lightbox doesn't work - yet. -->
  
<div id="myCarousel" class="carousel slide" data-ride="carousel">
	<!-- Large image -->
  <div class="carousel-inner">
	<?php 
		$dem = 0;
		foreach ( $items as $image ) { 
		$dem++;
		?>
		<?php if($dem == 1) { ?>
		  <div class="large-image carousel-item active">
			<img id="toggleImage" src="<?php echo $image['url'];?>" style="width:100%">
		  </div>
		<?php } ?>
			<div class="large-image carousel-item">
			<img id="toggleImage" src="<?php echo $image['url'];?>" style="width:100%">
		  </div> 
		
	<?php } ?>


  </div>
</div>

<!-- Carousel Navigation -->
<div id="carousel-thumbs" class="carousel slide" data-ride="carousel">
	
  <div class="carousel-inner">
	  
    <div class="carousel-item active">
      <div class="row mx-0">
		<?php 
		$i = 0;
		foreach ( $items as $image ) { 
		$i++;
		if ($i == 7) { 
			break; 
		} ?>
        <div id="carousel-selector-<?php echo $i;?>" class="thumb col-2 px-1 py-2 selected" data-target="#myCarousel" data-slide-to="0">
			 <img src="<?php echo $image['url'];?>" class="img-fluid" alt="...">
		</div>
		<?php } ?>
      </div>
    </div>
    <div class="carousel-item">
		
      <div class="row mx-0">
        <div id="carousel-selector-6" class="thumb col-2 px-1 py-2" data-target="#myCarousel" data-slide-to="6">
          <img src="https://source.unsplash.com/uanoYn1AmPs/600x400/" class="img-fluid" alt="...">
        </div>
        <div id="carousel-selector-7" class="thumb col-2 px-1 py-2" data-target="#myCarousel" data-slide-to="7">
          <img src="https://source.unsplash.com/_snqARKTgoc/600x400/" class="img-fluid" alt="...">
        </div>
        <div id="carousel-selector-8" class="thumb col-2 px-1 py-2" data-target="#myCarousel" data-slide-to="8">
          <img src="https://source.unsplash.com/M9F8VR0jEPM/600x400/" class="img-fluid" alt="...">
        </div>
        <div id="carousel-selector-9" class="thumb col-2 px-1 py-2" data-target="#myCarousel" data-slide-to="9">
          <img src="https://source.unsplash.com/Q1p7bh3SHj8/600x400/" class="img-fluid" alt="...">
        </div>
        <div class="col-2 px-1 py-2"></div>
        <div class="col-2 px-1 py-2"></div>
      </div>
    </div>
  </div>
  <a class="carousel-control-prev" href="#carousel-thumbs" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"><i class="fas fa-angle-left"></i></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carousel-thumbs" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"><i class="fas fa-angle-right"></i></span>
    <span class="sr-only">Next</span>
  </a>
	
</div>
<!-- #Carousel Navigation -->
</div> <!-- /row -->
</div> <!-- /container -->
