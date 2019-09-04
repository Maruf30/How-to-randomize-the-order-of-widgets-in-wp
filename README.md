# How-to-randomize-the-order-of-widgets-in-wp



add_filter ('sidebars_widgets', 'wcs_randomize_widget_order');
  
function wcs_randomize_widget_order($sidebars_widgets) {
    $sidebar = 'sidebar'; // Replace 'sidebar' with the name of the widget you want to shuffle
    if (isset($sidebars_widgets[$sidebar]) && !is_admin()) {
        shuffle ($sidebars_widgets[$sidebar]);
    }
    return $sidebars_widgets;
}



If you want to randomize the widgets in all your sidebars, you can use:


add_filter ('sidebars_widgets', 'wcs_randomize_widget_order');
  
function wcs_randomize_widget_order($sidebars_widgets) {
    if (!is_admin()) {
        foreach ($sidebars_widgets as &$widget) {
            shuffle ($widget);
        }
    }
    return $sidebars_widgets;
}
