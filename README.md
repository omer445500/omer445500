
<!DOCTYPE html>
<html>
<head>
	<title>ZType</title>
	<link rel="stylesheet" type="text/css" href="media/landing.css?v2"/>
	<link rel="shortcut icon" href="media/favicon.png" type="image/png">
	<link rel="icon" href="media/favicon.png" type="image/png">
	<meta name="viewport" content="width=480, minimal-ui"/>

	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:site" content="@phoboslab" />
	<meta property="og:url" content="https://zty.pe/" />
	<meta property="og:title" content="ZType – Type to Shoot" />
	<meta property="og:description" content="Load your own text." />
	<meta property="og:image" content="https://zty.pe/media/ztype-card.png" />
	<script src="https://www.google.com/recaptcha/api.js" async defer></script>
</head>
<body>
	<div id="page">
		<div id="content">
			<img src="media/ztype.png" id="logo"/>
			
			<h1>Transform any Website<br/> into a typing game</h1>

			<form action="/" method="post" id="form">
				<div>
					<input placeholder="http://…" type="text" id="url" name="url"/>
				</div>
				<div>
					<textarea placeholder="…or paste your own text. Each sentence becomes a wave of enemies." id="text" name="text"></textarea>
				</div>

				<div>
					<label class="check">
						<input type="checkbox" name="caseSensitive"/>
						Case Sensitive (requires typing uppercase letters)
					</label>
				</div>
				<div>
					<label class="check">
						<input type="checkbox" name="punctuation"/>
						Enable punctuations and symbols
					</label>
				</div>
				<div>
					<label class="check">
						<input type="checkbox" name="numbers"/>
						Enable numbers
					</label>
				</div>


				<div 
					class="g-recaptcha" 
					data-sitekey="6Leq16AUAAAAAJ6bItA2g1REP1Ri1YuUEBJomMzl" 
					data-theme="dark"></div>

				<div id="warn" class="warn">
									</div>
				
				<div>
					<button role="submit">Play!</button>
				</div>
			</form>

			<h2>Examples</h2>
			<p>
				<a href="?text=972f9220491af002">The Cat In The Hat</a>
				<span class="difficulty">(easy)</span>
			</p>
			<p>
				<a href="?text=72cbee8ed3ba9388">Alice in Wonderland</a>
				<span class="difficulty">(medium)</span>
			</p>
			<p>
				<a href="?url=https://simple.wikipedia.org/wiki/Special:RandomInCategory/Good_articles">Random Wikipedia Article – Simple English</a>
				<span class="difficulty">(medium)</span>
			</p>
			<p>
				<a href="?url=https://en.wikipedia.org/wiki/Special:RandomInCategory/Good_articles">Random Wikipedia Article</a>
				<span class="difficulty">(probably hard)</span>
			</p>
			<p>
				<a href="?text=11e5dad15e3dca9b">Moby Dick</a>
				<span class="difficulty">(hard)</span>
			</p>
			<p>
				<a href="?text=21bb8f1868f879f8">Donald Trump’s Speech, South Carolina</a>
				<span class="difficulty">(incomprehensible)</span>
			</p>
			<p>or</p>
			<p>
				<a href="/">The Default, Random Wordlist</a>
			</p>
		</div>
	</div>

	<script type="text/javascript">
		document.getElementById('form').addEventListener('submit', function(ev){
			var url = document.getElementById('url').value;
			var text = document.getElementById('text').value;
			var words = text.split(/\s+/);

			if (url.length > 0) {
				if (!url.match(/\b(https?:\/\/(?:www\.)?|www\.)([^\s()<>]+(?:\([\w\d]+\)|([^,\.\(\)<>!?\s]|\/)))/)) {
					document.getElementById('warn').innerHTML = 'Sorry, the URL does not seem to be valid.';
					ev.preventDefault();
					return false;
				}
			}
			else if (text.length > 0) {
				if (words.length < 2 || text.length < 5) {
					document.getElementById('warn').innerHTML = 'Sorry, your text is too short. Two words minimum.';
					ev.preventDefault();
					return false;
				}
			}
			else {
				document.getElementById('warn').innerHTML = 'Please enter a URL or some text.';
				ev.preventDefault();
				return false;
			}
		});
	</script>

	<div id="footer">
		ZType (c) – <a href="http://phoboslab.org/" target="_blank">phoboslab.org</a>
	</div>
</body>
</html>
