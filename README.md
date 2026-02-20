
```php

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

