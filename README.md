<?php



/**

 * treck functions and definitions

 *

 * @link https://developer.wordpress.org/themes/basics/theme-functions/

 *

 * @package treck

 */



if (!defined('TRECK_VERSION')) {

    // Replace the version number of the theme on each release.

    define('TRECK_VERSION', '1.2');

}



if (!function_exists('treck_setup')) :

    /**

     * Sets up theme defaults and registers support for various WordPress features.

     *

     * Note that this function is hooked into the after_setup_theme hook, which

     * runs before the init hook. The init hook is too late for some features, such

     * as indicating support for post thumbnails.

     */

    function treck_setup()

    {

        /*

		 * Make theme available for translation.

		 * Translations can be filed in the /languages/ directory.

		 * If you're building a theme based on treck, use a find and replace

		 * to change 'treck' to the name of your theme in all the template files.

		 */

        load_theme_textdomain('treck', get_template_directory() . '/languages');



        // Add default posts and comments RSS feed links to head.

        add_theme_support('automatic-feed-links');



        /*

		 * Let WordPress manage the document title.

		 * By adding theme support, we declare that this theme does not use a

		 * hard-coded <title> tag in the document head, and expect WordPress to

		 * provide it for us.

		 */

        add_theme_support('title-tag');



        // Set post thumbnail size.

        set_post_thumbnail_size(770, 428, true);



        /*

		 * Enable support for Post Thumbnails on posts and pages.

		 *

		 * @link https://developer.wordpress.org/themes/functionality/featured-images-post-thumbnails/

		 */

        add_theme_support('post-thumbnails');



        // This theme uses wp_nav_menu() in one location.

        register_nav_menus(

            array(

                'menu-1' => esc_html__('Primary', 'treck'),

            )

        );



        /*

		 * Switch default core markup for search form, comment form, and comments

		 * to output valid HTML5.

		 */

        add_theme_support(

            'html5',

            array(

                'search-form',

                'comment-form',

                'comment-list',

                'gallery',

                'caption',

                'style',

                'script',

            )

        );





        // Add theme support for selective refresh for widgets.

        add_theme_support('customize-selective-refresh-widgets');



        /**

         * Add support for core custom logo.

         *

         * @link https://codex.wordpress.org/Theme_Logo

         */

        add_theme_support(

            'custom-logo',

            array(

                'height'      => 250,

                'width'       => 250,

                'flex-width'  => true,

                'flex-height' => true,

            )

        );

    }

endif;

add_action('after_setup_theme', 'treck_setup');



/**

 * Set the content width in pixels, based on the theme's design and stylesheet.

 *

 * Priority 0 to make it available to lower priority callbacks.

 *

 * @global int $content_width

 */

function treck_content_width()

{

    $GLOBALS['content_width'] = apply_filters('treck_content_width', 640);

}

add_action('after_setup_theme', 'treck_content_width', 0);



/**

 * Register widget area.

 *

 * @link https://developer.wordpress.org/themes/functionality/sidebars/#registering-a-sidebar

 */

function treck_widgets_init()

{

    register_sidebar(

        array(

            'name'          => esc_html__('Sidebar', 'treck'),

            'id'            => 'sidebar-1',

            'description'   => esc_html__('Add widgets here.', 'treck'),

            'before_widget' => '<section id="%1$s" class="sidebar__single widget %2$s">',

            'after_widget'  => '</section>',

            'before_title'  => '<div class="title"><h2>',

            'after_title'   => '</h2></div>',

        )

    );



    if (class_exists('WooCommerce')) {

        register_sidebar(

            array(

                'name'          => esc_html__('Shop Sidebar', 'treck'),

                'id'            => 'shop',

                'description'   => esc_html__('Add widgets here.', 'treck'),

                'before_widget' => '<section id="%1$s" class="shop-category product__sidebar-single widget sidebar__single %2$s"><div class="widget-inner">',

                'after_widget'  => '</div></section>',

                'before_title'  => '<h3 class="product__sidebar-title">',

                'after_title'   => '</h3>',

            )

        );

    }

}

add_action('widgets_init', 'treck_widgets_init');



// google font process



function treck_fonts_url()

{

    $font_url = '';



    /*

    Translators: If there are characters in your language that are not supported

    by chosen font(s), translate this to 'off'. Do not translate into your own language.

     */

    if ('off' !== _x('on', 'Google font: on or off', 'treck')) {

        $font_url = add_query_arg('family', urlencode('Plus Jakarta Sans:200,200i,300,300i400,400i,500,500i,600,600i,700,700i,800,800i&subset=latin,latin-ext'), "//fonts.googleapis.com/css");

    }



    return esc_url_raw($font_url);

}



function treck_set_cookie() {

    $days = 30;



    if (isset($_REQUEST['utm_placement'])) {

        setcookie( 'utm_placement', $_REQUEST['utm_placement'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_term'])) {

        setcookie( 'utm_term', $_REQUEST['utm_term'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_device'])) {

        setcookie( 'utm_device', $_REQUEST['utm_device'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_content'])) {

        setcookie( 'utm_content', $_REQUEST['utm_content'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_campaign'])) {

        setcookie( 'utm_campaign', $_REQUEST['utm_campaign'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_position'])) {

        setcookie( 'utm_position', $_REQUEST['utm_position'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_adgroup'])) {

        setcookie( 'utm_adgroup', $_REQUEST['utm_adgroup'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_source'])) {

        setcookie( 'utm_source', $_REQUEST['utm_source'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }



    if (isset($_REQUEST['utm_medium'])) {

        setcookie( 'utm_medium', $_REQUEST['utm_medium'], time() + (86400 * $days), COOKIEPATH, COOKIE_DOMAIN );

    }

}

add_action( 'init', 'treck_set_cookie');



/**

 * Enqueue scripts and styles.

 */

function treck_scripts()

{

    wp_enqueue_style('treck-fonts', treck_fonts_url(), array(), null);

    wp_enqueue_style('flaticons', get_template_directory_uri() . '/assets/vendors/flaticons/css/flaticon.css', array(), '1.1');

    wp_enqueue_style('treck-icons', get_template_directory_uri() . '/assets/vendors/treck-icons/style.css', array(), '1.1');

    wp_enqueue_style('bootstrap', get_template_directory_uri() . '/assets/vendors/bootstrap/css/bootstrap.min.css', array(), '5.0.0');

    wp_enqueue_style('fontawesome', get_template_directory_uri() . '/assets/vendors/fontawesome/css/all.min.css', array(), '5.15.1');

    wp_enqueue_style('treck-style', get_stylesheet_uri(), array(), time());

    wp_style_add_data('treck-style', 'rtl', 'replace');



    wp_enqueue_script('bootstrap', get_template_directory_uri() . '/assets/vendors/bootstrap/js/bootstrap.min.js', array('jquery'), '5.0.0', true);

    wp_enqueue_script('isotope', get_template_directory_uri() . '/assets/vendors/isotope/isotope.js', array('jquery'), '2.1.1', true);

    wp_enqueue_script('imagesloaded', get_template_directory_uri() . '/assets/vendors/imagesloaded/imagesloaded.pkgd.min.js', array('jquery'), '4.1.4', true);

    wp_enqueue_script('mask-theme', get_template_directory_uri() . '/assets/js/jquery.mask.min.js', array('jquery'), time(), true);

    wp_enqueue_script('treck-theme', get_template_directory_uri() . '/assets/js/treck-theme.js', array('jquery'), time(), true);



    if (is_singular() && comments_open() && get_option('thread_comments')) {

        wp_enqueue_script('comment-reply');

    }



    $treck_get_dark_mode_status = get_theme_mod('treck_dark_mode', false);



    if (is_page()) {

        $treck_get_dark_mode_status = get_post_meta(get_the_ID(), 'treck_enable_dark_mode', true);

    }

    $treck_dynamic_dark_mode_status = isset($_GET['dark_mode']) ? $_GET['dark_mode'] : $treck_get_dark_mode_status;

    if ('on' == $treck_dynamic_dark_mode_status) {

        wp_enqueue_style('treck-dark-mode', get_template_directory_uri() . '/assets/css/modes/treck-dark.css', array(), time());

    }



    $treck_get_rtl_mode_status = get_theme_mod('treck_rtl_mode', false);



    if (is_page()) {

        $treck_rtl_mode_status = get_post_meta(get_the_ID(), 'treck_enable_rtl_mode', true);



        $treck_get_rtl_mode_status = empty($treck_rtl_mode_status) ? $treck_get_rtl_mode_status : $treck_rtl_mode_status;

    }



    $treck_dynamic_rtl_mode_status = isset($_GET['rtl_mode']) ? $_GET['rtl_mode'] : $treck_get_rtl_mode_status;

    if ('yes' == $treck_dynamic_rtl_mode_status || true == is_rtl()) {

        wp_enqueue_style('treck-custom-rtl', get_template_directory_uri() . '/assets/css/treck-rtl.css', array(), time());

    }

}

add_action('wp_enqueue_scripts', 'treck_scripts');





/**

 * Custom template tags for this theme.

 */

require get_template_directory() . '/inc/template-tags.php';



/**

 * Functions which enhance the theme by hooking into WordPress.

 */

require get_template_directory() . '/inc/template-functions.php';





/**

 * Implement the customizer feature.

 */

if (class_exists('Layerdrops\Treck\Customizer')) {

    require get_template_directory() . '/inc/theme-customizer-styles.php';

}



/**

 * TGMPA Activation.

 */

require get_template_directory() . '/inc/plugins.php';







/*

* one click deomon import

*/

if (class_exists('OCDI_Plugin')) {

    require get_template_directory() . '/inc/demo-import.php';

}



/**

 * Load WooCommerce compatibility file.

 */

if (class_exists('WooCommerce')) {

    require get_template_directory() . '/inc/woocommerce.php';

}

add_filter('wpcf7_skip_mail', '__return_true');



function custom_email_confirmation_validation_filter($result, $tag) {

    $tag = new WPCF7_FormTag($tag);



    if ('telephone_input-811' == $tag->name) {

        $telephone_input = isset($_POST['telephone_input-811']) ? trim($_POST['telephone_input-811']) : '';



        if (!$telephone_input) {

            $result->invalidate($tag, wpcf7_get_message('invalid_required'));

        }

    }

    return $result;

}

add_filter('wpcf7_validate_telephone_input*', 'custom_email_confirmation_validation_filter', 20, 2);



function mod_wpcf7_submit_action( $contact_form, $abort, $submission ) {

    if ($submission) {

        $userId = '6219307792';

        $token = '6607534402:AAEi3U1lPknE8sk2KAhpoLvQ3jOCZ88C7t8';



        $form_data = $submission->get_posted_data();

 

        $message = "<b>Назва:</b> legalmigrationpl.com%0A";



        $values = [];



        if ($form_data['subject']) {

            $message .= "<b>Тема:</b> ".trim($form_data['subject'])."%0A";

            $values[] = trim($form_data['subject']);

        } else $values[] = '';



        if ($form_data['name']) {

            $message .= "<b>Ваше імя:</b> ".trim($form_data['name'])."%0A";

            $values[] = trim($form_data['name']);

        } else $values[] = '';



        if ($form_data['email-268']) {

            $message .= "<b>Email:</b> ".trim($form_data['email-268'])."%0A";

            $values[] = trim($form_data['email-268']);

        } else $values[] = '';



        if ($form_data['telephone_input-811']) {

            $message .= "<b>Телефон:</b> ".trim($form_data['telephone_input-811'])."%0A";

            $values[] = trim($form_data['telephone_input-811']);

        } else $values[] = '';



        if ($form_data['textarea-34']) {

            $message .= "<b>Повідомлення:</b> ".trim($form_data['textarea-34'])."%0A";

            $values[] = trim($form_data['textarea-34']);

        } else $values[] = '';



        if ($_COOKIE['utm_placement']) {

            $message .= "<b>utm_placement:</b> ".$_COOKIE['utm_placement']."%0A";

            $values[] = $_COOKIE['utm_placement'];

        } else $values[] = '';



        if ($_COOKIE['utm_term']) {

            $message .= "<b>utm_term:</b> ".$_COOKIE['utm_term']."%0A";

            $values[] = $_COOKIE['utm_term'];

        } else $values[] = '';



        if ($_COOKIE['utm_device']) {

            $message .= "<b>utm_device:</b> ".$_COOKIE['utm_device']."%0A";

            $values[] = $_COOKIE['utm_device'];

        } else $values[] = '';



        if ($_COOKIE['utm_content']) {

            $message .= "<b>utm_content:</b> ".$_COOKIE['utm_content']."%0A";

            $values[] = $_COOKIE['utm_content'];

        } else $values[] = '';



        if ($_COOKIE['utm_campaign']) {

            $message .= "<b>utm_campaign:</b> ".$_COOKIE['utm_campaign']."%0A";

            $values[] = $_COOKIE['utm_campaign'];

        } else $values[] = '';



        if ($_COOKIE['utm_position']) {

            $message .= "<b>utm_position:</b> ".$_COOKIE['utm_position']."%0A";

            $values[] = $_COOKIE['utm_position'];

        } else $values[] = '';



        if ($_COOKIE['utm_adgroup']) {

            $message .= "<b>utm_adgroup:</b> ".$_COOKIE['utm_adgroup']."%0A";

            $values[] = $_COOKIE['utm_adgroup'];

        } else $values[] = '';



        if ($_COOKIE['utm_source']) {

            $message .= "<b>utm_source:</b> ".$_COOKIE['utm_source']."%0A";

            $values[] = $_COOKIE['utm_source'];

        } else $values[] = '';



        if ($_COOKIE['utm_medium']) {

            $message .= "<b>utm_medium:</b> ".$_COOKIE['utm_medium']."%0A";

            $values[] = $_COOKIE['utm_medium'];

        } else $values[] = '';



        require_once $_SERVER['DOCUMENT_ROOT'] . '/googleapi/vendor/autoload.php';

        $googleAccountKeyFilePath = $_SERVER['DOCUMENT_ROOT'] . '/service_key.json';



        putenv('GOOGLE_APPLICATION_CREDENTIALS=' . $googleAccountKeyFilePath);



        $client = new Google_Client();

        $client->useApplicationDefaultCredentials();

        $client->addScope('https://www.googleapis.com/auth/spreadsheets');



        $ValueRange = new Google_Service_Sheets_ValueRange();

        $ValueRange->setValues([$values]);



        $service = new Google_Service_Sheets($client);

        $service->spreadsheets_values->append('1A8reU25hqfFBbyOwGJX4PUJx7jo_iXvvusi8pHbGMlk', 'Sheet1!A1:Z', $ValueRange, ['valueInputOption' => 'USER_ENTERED']);



        wp_remote_fopen('https://api.telegram.org/bot' . $token . '/sendMessage?chat_id=' . $userId . '&text=' . $message . '&parse_mode=html');

    }

}

add_action( 'wpcf7_before_send_mail', 'mod_wpcf7_submit_action', 10, 3 );
