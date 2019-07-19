### jinja-assets-compressor
---
https://github.com/jaysonsantos/jinja-assets-compressor

```
```

```sh
pip install jac
npm install -g less
npm install -g coffee-script
gem install sass
export CFLAGS=-Qunused-arguments
```

```
{% compress 'css' %}
<style type="text/sass">
sass stuff
</style>
<link rel="stylesheet" type="text/sass" href="file.sass">
{% endcompress %}

{% compress 'js' %}
<script type="text/coffeescript">
coffee stuff
</script>
<script type-"text/coffeescript" src="file.coffee"></script>
{% endcompress %}
```


