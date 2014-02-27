# smartReadFile

For reading media file through a PHP controller

## Code example:

This code is in the api.php file. You should refer to the api.php file for the latest version of usage example.

```php
/*
 * API Example
 */

require_once('smartReadFile.php');

// Get name passed via URL
$filename = $_GET['f'];

// Usually this would be hidden above the web server root. EG., '/hidden/media/'
$base = 'media/';

// Whitelist filename characters
$ok = preg_match('/^[-A-Za-z0-9_.]+$/', $filename);

// Ignore requests that smell funny
if (!$ok) {
	header ("HTTP/1.1 404 Not Found");
	die();
}

$file = explode('.', $filename);

// Get the type by file extension
switch ($file[count($file)-1]) {
	case 'mp3':
		$type = 'audio/mpeg';
		break;
	case 'ogg':
		$type = 'audio/ogg';
		break;
	case 'oga':
		$type = 'audio/ogg';
		break;
	case 'm4a':
		$type = 'audio/mp4';
		break;
	case 'm4v':
		$type = 'video/mp4';
		break;
	case 'mp4':
		$type = 'video/mp4';
		break;
	case 'webm':
		$type = 'video/webm';
		break;
	case 'ogv':
		$type = 'video/ogg';
		break;
}

$path = $base . $filename;

// Call smartReadFile
smartReadFile($path, $filename, $type);
```

## License

MIT License.

## Kudos to the creators!

The development history:

* Alpha: gaosipov of [php.net](http://php.net/manual/en/function.readfile.php#86244) User Contributed Notes
* Beta: Joe Lencioni of [Shifting Pixel](http://shiftingpixel.com/)
* 1.0: Eoin of [bitesizeirishgaelic.com](http://www.bitesizeirishgaelic.com/)

## Media Copyright

The media used in this demo is owned by:

* **Bubble** © 2003 Miaow / Arnaud Laflaquiere - [MiaowMusic.com](http://www.miaowmusic.com/)
* **Big Bubk Bunny** © 2008 Blender Foundation - [bigbuckbunny.org](http://www.bigbuckbunny.org/)
