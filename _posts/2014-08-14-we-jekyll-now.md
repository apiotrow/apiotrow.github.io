---
layout: post
title: We Jekyll Now
---

Just migrated this blog from Wordpress.com to my GitHub. Using this thing called Jekyll. It's pretty hardcore. When I do things through the command line I feel like I'm hacking into The Matrix. It took a long journey of Googling to get it running. It went like this:

	
{% highlight c# %}
void InstallJekyll(){
	UpdateGem();
	InstallJekyll();
	MakeABlog();
}

void UpdateGem(){
	try{
		gem install rubygems-update;
		update_rubygems;
	}catch(IOException e){
		string err = "Fetching: eventmachine-1.0.3.gem (100%) ERROR:  While executing gem ... (Gem::FilePermissionError) You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.";
		if(e.ToString() == err){
			InstallRbenv();
			UpdateGem();
			//infinite loops are best loops
		}

	}
}

void InstallRbenv(){
	goto https://github.com/sstephenson/rbenv;
	git clone https://github.com/sstephenson/rbenv.git ~/.rbenv;
	echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile;
	echo 'eval "$(rbenv init -)"' >> ~/.bash_profile;
	type rbenv;
}

void InstallJekyll(){
	gem install jekyll;
}

void MakeABlog(){
	???;
	FuckItJustFindATemplate();
}

void FuckItJustFindATemplate(){
	google "jekyll template";
	click Poole's GitHub;
	mkdir thisIsMyBlogIMadeWithNoHelp;
	cd thisIsMyBlogIMadeWithNoHelp;
	git clone git@github.com:poole/poole.git;
	cp -a /poole/. .;
	rm -r poole;
	rm -r .git;
	git init;
	git remote add origin git@github.com:apiotrow/apiotrow.github.io.git;
	git add -A;
	git commit -m "First commit. Really proud of all this stuff I made completely on my own";
	git push -u origin master;
}

{% endhighlight %}


And now I have this blog. 

![matrix]({{ site.url }}/assets/2014-08-14/neodecodelogo.jpg)![link]({{ site.url }}https://rawgit.com/apiotrow/UnityExperiments/master/balance/balance.html)
