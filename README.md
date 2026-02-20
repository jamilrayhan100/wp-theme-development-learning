
# WP_Query for category from post

```php


// get all category 
function kindaid_all_cat($category = 'category'){
   $categories = get_categories( array(
      'taxonomy' => $category,
      'orderby' => 'name',
      'order'   => 'ASC',
   ) );
   $cat_list = [];
   foreach($categories as $cat){
      $cat_list[$cat->slug] = $cat->name;
   }
   return $cat_list;
}


// get all post 
function kindaid_all_post($post_type_name = 'post'){
    $posts = get_posts( array(
        'post_type' => $post_type_name,
        'orderby' => 'name',
        'order'   => 'ASC',
        'posts_per_page'   => -1,
    ) );
    $posts_list = [];
    foreach($posts as $post){
        $posts_list[$post->ID] = $post->post_title;
    }
    return $posts_list;
}





// WP_Query arguments
  $args = array(
      'post_type'              => array('post'),
      'post_status'            => array('publish'), 
      'posts_per_page'         => '3', 
      'order'                  => 'DESC',
      'orderby'                => 'date',				
    
  );
  // The Query
  $query = new WP_Query($args);



// WP_Query code with loop 
<?php if(!empty($categorie)) : 
    $limited_categories = array_slice($categorie, 0, 2);		
    $has_second = count( $limited_categories ) > 1;								
    ?>
    <?php foreach($limited_categories as $key => $cat) : ?>
        <span class="<?php echo ($has_second && $key === 0) ? 'dvdr' : ''; ?>">
          <a href="<?php echo esc_url(get_category_link($cat->term_id)); ?>">
            <?php echo esc_html($cat->name); ?>
          </a>
        </span>
    <?php endforeach; ?>
<?php endif; ?>


```

