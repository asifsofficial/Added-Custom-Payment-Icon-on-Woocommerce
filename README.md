# Added Custom Payment Icon on Woocommerce

## Location:
```
functions.php
```

```
// Payment Methord Custom LOGO START
add_filter( 'woocommerce_gateway_icon', 'custom_payment_gateway_icons', 10, 2 );
function custom_payment_gateway_icons( $icon, $gateway_id ){

    foreach( WC()->payment_gateways->get_available_payment_gateways() as $gateway )
        if( $gateway->id == $gateway_id ){
            $title = $gateway->get_title();
            break;
        }

    // The path (subfolder name(s) in the active theme)
    $path = get_stylesheet_directory_uri(). '/assets';

    // Setting (or not) a custom icon to the payment IDs
    if($gateway_id == 'bacs')
        $icon = '<img src="' . WC_HTTPS::force_https_url( "Your Logo/icon url" ) . '" alt="' . esc_attr( $title ) . '" />';
    elseif( $gateway_id == 'cheque' )
        $icon = '<img src="' . WC_HTTPS::force_https_url( "Your Logo/icon url" ) . '" alt="' . esc_attr( $title ) . '" />';
    elseif( $gateway_id == 'cod' )
        $icon = '<img src="' . WC_HTTPS::force_https_url( "Your Logo/icon url" ) . '" alt="' . esc_attr( $title ) . '" />';
    elseif( $gateway_id == 'uddoktapay' )
        $icon = '<img src="' . WC_HTTPS::force_https_url( "Your Logo/icon url" ) . '" alt="' . esc_attr( $title ) . '" />';
    elseif( $gateway_id == 'ppec_paypal' || 'paypal' )
        $icon = '<img src="' . WC_HTTPS::force_https_url( "Your Logo/icon url" ) . '" alt="' . esc_attr( $title ) . '" />';
        return $icon;

    return $icon;
}
```
