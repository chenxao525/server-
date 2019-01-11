function sc_send(  $text , $desp = '' , $key = '[SCKEY(登入后可见)]'  )
{
	$postdata = http_build_query(
    array(
        'text' => $text,
        'desp' => $desp
    )
);

$opts = array('http' =>
    array(
        'method'  => 'POST',
        'header'  => 'Content-type: application/x-www-form-urlencoded',
        'content' => $postdata
    )
);
$context  = stream_context_create($opts);
return $result = file_get_contents('https://sc.ftqq.com/'.$key.'.send', false, $context);

}
