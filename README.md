
```php

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

