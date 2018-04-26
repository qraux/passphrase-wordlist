# Overview
This is a project to build a massive wordlist using passphrases for cracking password hashes. Most of the wordlists I know of (rockyou, exploitin, crackstation, etc) contain single-word passwords. People are getting smarter and using phrases instead.

**For Cracking: You need only the "passphrases" file.** This is stored in Git Large File Storage (glfs), so download via <a download href="https://github.com/initstring/passphrase-wordlist/raw/master/passphrases.txt">this link</a> or use git clone if you have the glfs extensions installed.

I've also included a hashcat rule file that seems to make sense for passphrases. You can combine it with another rule list like [Hob0](https://github.com/praetorian-inc/Hob0Rules) or [OneRule](https://github.com/NotSoSecure/password_cracking_rules).

# Sources Used
So far, I've scraped the following: <br>
- [15,000 Useful Phrases](https://www.gutenberg.org/ebooks/18362)
- Urban Dictionary dataset pulled Dec 09 2017 using [this great script](https://github.com/mattbierner/urban-dictionary-word-list).
- Song lyrics for Rolling Stone's "top 100" artists using my [lyric scraping tool](https://github.com/initstring/lyricpass).
- Movie titles and lines from this [Cornell project](http://www.cs.cornell.edu/~cristian//Cornell_Movie-Dialogs_Corpus.html).
- "Titles" from the [IMDB dataset](https://www.kaggle.com/orgesleka/imdbmovies) on Kaggle.
- [Quotables](https://www.kaggle.com/alvations/quotables) dataset on Kaggle.
- [MemeTracker](https://www.kaggle.com/snap/snap-memetracker) dataset from Kaggle.
- [Wikipedia Article Titles](https://www.kaggle.com/residentmario/wikipedia-article-titles) dataset from Kaggle.
- A few random "top phrases / top quotes" sites

# Cleaning sources
Check out the script [clean.sh](https://github.com/initstring/passphrase-cracker/blob/master/clean.sh) to see how I've cleaned the raw sources. You can find the pre-cleaned data [here](https://github.com/initstring/passphrase-cracker/tree/master/raw-sources).

# Hashcat Rules
Given the phrase `one fish two fish red fish blue fish` the hashcat rules will output the following:
```
one fish two fish red fish blue fish
one-fish-two-fish-red-fish-blue-fish
one.fish.two.fish.red.fish.blue.fish
one,fish,two,fish,red,fish,blue,fish
one_fish_two_fish_red_fish_blue_fish
onefishtwofishredfishbluefish
One fish two fish red fish blue fish
ONE FISH TWO FISH RED FISH BLUE FISH
oNE FISH TWO FISH RED FISH BLUE FISH
One Fish Two Fish Red Fish Blue Fish
OneFishTwoFishRedFishBlueFish
One-Fish-Two-Fish-Red-Fish-Blue-Fish
One.Fish.Two.Fish.Red.Fish.Blue.Fish
One,Fish,Two,Fish,Red,Fish,Blue,Fish
One_Fish_Two_Fish_Red_Fish_Blue_Fish
```

A great thing about hashcat is that you can feed it two rule files. So, if you want to also get fancy with adding numbers at the end, swapping l33tsp33k in, etc, simply add another `-r` AFTER supplying this rule.

Enjoy!
