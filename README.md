# mattermost
Add/ Delete users from channels with API

require 'vendor/autoload.php';

use \Gnello\Mattermost\Driver;

$container = new \Pimple\Container([
"driver" => [
"url" => "https://your-mattermost-url.com",
"login_id" => "email@domain.com",
"password" => "Password1",
]
]);

$driver = new Driver($container);
$driver->authenticate();

$teamID = "zWEyrTZ7GZ22aBSfoX60iWryTY";
$userID = "NqCSr5HMDZjrWS74IEmedvlOYf";

$resp = $driver->getTeamModel()->removeUser($teamID, $userID);

if ($resp->getStatusCode() == 200) {
$ok = json_decode($resp->getBody())->status;
}
