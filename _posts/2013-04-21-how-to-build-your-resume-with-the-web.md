---
layout: post
title: How to build your résumé with the web
---
If you need a job and aren't famous, you will likely need a résumé. If you can't be bothered, you can cook one up in LibreOffice Writer. If you want a high degree of stylistic precision and a clean separation between content and presentation, you can use LaTeX. In my case, I did not want to invest my time into mastering a complex technology just to create one single-page document. Instead, I turned to the power of the web to build my résumé, using JSON, HTML, CSS, [Handlebars.js](http://handlebarsjs.com) and [PhantomJS](http://phantomjs.org). It resulted in [this PDF file](https://www.dropbox.com/s/xlduz7ka5qj8hwd/resume.pdf). I will demonstrate the process.

Get Node.js from [here](http://nodejs.org/download) or through your package manager. Create an empty directory for your project, and inside it run the Unix shell command `npm install phantomjs handlebars; wget https://raw.github.com/skofo/resume/master/build.js; chmod +x build.js; wget http://meyerweb.com/eric/tools/css/reset/reset.css`. This will locally install the required modules, download the build script, set the build script as executable, and download meyerweb's reset stylesheet. If you're on Windows, run the part before the first semicolon and download the script and stylesheet manually.

It's a good idea to start with a rough draft of your résumé to get an idea of how you want to express and organize your information.

Put your information into a JSON file ([example](https://github.com/skofo/resume/blob/master/data.json)) and write a Handlebars template to organize it with a reference to the reset stylesheet and your own stylesheet ([example](https://github.com/skofo/resume/blob/master/template.handlebars)). Then run `./build.js --keep-html` to generate an unstyled HTML file as well as a matching PDF file.

Now you get to write your stylesheet. This is no different from styling a regular web page, except that the body should have an explicit width (at least ~650px) and its margin set to auto. Given that, your generated PDF file should look almost exactly like your web page and fit neatly between the page margins. Speaking of margins, you can set the paper and margin sizes on lines 5 and 6 of build.js ([more info here](https://github.com/ariya/phantomjs/wiki/API-Reference-WebPage#wiki-webpage-paperSize)).

That's all there is to it. Just rerun that last command as many times as you need to while you're working on the style, then in the future you can run it without the argument after changing the JSON data.
