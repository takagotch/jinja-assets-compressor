### jinja-assets-compressor
---
https://github.com/jaysonsantos/jinja-assets-compressor

```py 
import jinja2

from jac import CompressorExtension

env = jinja2.Environment(extensions=[CompressorExtension])
env.compressor_output_dir = './static/dist'
env.compressor_static_prefix = '/static'
env.compressor_source_dirs = './static_files'


from jac.contrib.flask import JAC

app = Flask(__name__)
app.config['COMPRESSOR_DEBUG'] = app.config.get('DEBUG')
app.config['COMPRESSOR_OUTPUT_DIR'] = './static/dist'
app.config['COMPRESSOR_STATIC_PREFIX'] = '/static'
jac = JAC(app)


import sass

class CustomSassCompressor(object):
  """
  """
  
  @classmethod
  def compile(cls, text, cwd=None, **kwargs):
    
    include_paths = []
    if cwd:
      include_paths += [cwd]
      
    return sass.compile(string=text, include_paths=include_paths)
    
env.compressor_classes['text/sass'] = CustomSassCompressor

jac.set_compressor('text/sass', CustomSassCompressor)


from jac.compressors import SassCompressor

class CustomSassCompressor(SassCompressor):
  """
  """
  
  binary = '/usr/bin/sassc'
```

```sh
pip install jac
npm install -g less
npm install -g coffee-script
gem install sass
export CFLAGS=-Qunused-arguments

python -m jac.contrib.flask my_flask_module:create_app

virtualenv venv
. venv/bin/activate
pip install -r requirements_tests.txt
make coverage
make lint

pip install tox
tox
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

```json
{
  'text/css': LessCompressor,
  'text/coffeescript': CoffeScriptCompressor,
  'text/less': LessCompressor,
  'text/javascript': JavaScriptCompressor,
  'text/sass': SassCompressor,
  'text/scss': SassCompressor,
}

```
