---
layout: help
mirrorid: AdoptOpenJDK
category: help
---

# AdoptOpenJDK mirror guide

### Windows/macOS

Open [download page](https://{{ site.hostname }}/AdoptOpenJDK/) Choose your version and download the package.

### Ubuntu

Import gpg key

```
wget -qO - https://{{ site.hostname }}/AdoptOpenJDK/AdoptOpenJDK-gpg-public | sudo apt-key add -
```

Choose your Ubuntu version, and write the text content to `/etc/apt/sources.list.d/AdoptOpenJDK.list`.

<form class="form-inline">
<div class="form-group">
	<label>Choose your Ubuntu version: </label>
		<label>
    <select class="form-control" v-model="debrelease">
    <option value="bionic" selected>Ubuntu 18.04 LTS</option>
    <option value="focal">Ubuntu 20.04 LTS</option>
    </select>
		</label>
</div>
</form>

{% raw %}
<p></p>
<pre>
<code id="deb-bionic-content">deb https://{% endraw %}{{ site.hostname }}{% raw %}/AdoptOpenJDK/deb{% endraw %} {% raw %}{{debrelease}} main</code>
</pre>
{% endraw %}

Or copy the content, paste it in Terminal and press Enter to confirm.

{% raw %}
<p></p>
<pre>
<code class="language-bash" id="deb-focal-content">cat >>/home/AdoptOpenJDK.list<< EOF
deb https://{%endraw%}{{ site.hostname }}{%raw%}/AdoptOpenJDK/deb {{ debrelease }} main
EOF</code>
</pre>
{% endraw %}

Execute the `apt` command
```shell
sudo apt update
```

### CentOS

Write the text content to `/etc/yum.repos.d/AdoptOpenJDK.repo`.

```
[AdoptOpenJDK]
name=AdoptOpenJDK
baseurl=https://{{ site.hostname }}/AdoptOpenJDK/rpm/centos$releasever-$basearch/
enabled=1
gpgcheck=1
gpgkey=https://{{ site.hostname }}/AdoptOpenJDK/AdoptOpenJDK-gpg-public
```

Or copy the content, paste it in Terminal and press Enter to confirm.
```shell
cat >>/etc/yum.repos.d/AdoptOpenJDK.repo<< EOF
[AdoptOpenJDK]
name=AdoptOpenJDK
baseurl=https://{{ site.hostname }}/AdoptOpenJDK/rpm/centos$releasever-$basearch/
enabled=1
gpgcheck=1
gpgkey=https://{{ site.hostname }}/AdoptOpenJDK/AdoptOpenJDK-gpg-public
EOF
```

<form class="form-inline">
<div class="form-group">
	<label> Execute the </label>
	<label>
		<select class="form-control" v-model="yum_dnf">
    <option value="yum" selected>Centos 7</option>
    <option value="dnf">CentOS 8</option>
    </select>
	</label>
	<label> command </label>
</div>
</form>

{% raw %}
<p></p>
<pre>
<code class="language-bash" id="yum-dnf-content">{{ yum_dnf }} makecache</code>
</pre>
{% endraw %}

{% raw %}
<script>
 let vue = new Vue({
		 el: "#help-content",
		 data: {
				 debrelease: 'bionic',
				 yum_dnf: 'yum',
		 },
		 computed: {
		 }
 });
</script>
{% endraw %}
