## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/s40723247/s40723247.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/s40723247/s40723247.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

<!doctype html>
<html>
<head>
<meta charset="UTF-8">
<title>no.1</title>

<link rel="shortcut icon" href="css/favicon.ico">    
<link rel="stylesheet" type="text/css" href="css/bssite.css" media="screen" />
 
<script type="text/javascript" src="static/jquery-3.3.1.min.js" ></script>
<script type="text/javascript" src="static/jquery-ui.1.12.1.min.js" ></script>
<script type="text/javascript" src="static/pixi-4.8.2.min.js"></script>
<script type="text/javascript" src="static/buzz-1.2.1.js"></script>
<script type="text/javascript" src="static/brython-3.7.0.js"></script>
<script type="text/javascript" src="static/brython_stdlib-3.7.0.js"></script>
</head>
<body>
<script type="text/javascript">
window.onload=function(){
brython({debug:1, pythonpath:['static']});
}
</script>
<script type="text/python">
# 導入模組
from ggame import App, ImageAsset, Sprite, MouseEvent
from ggame import Color, Sound, LineStyle, RectangleAsset, CircleAsset, PolygonAsset, SoundAsset
from random import random, randint

up = 0
q = 0
life = 0
i = 0

def w(event):
     global up
     up = 1
    
def d(event):
     global q
     q = 1
    
def a(event):
     global life
     life = 1
     
class Bunny(Sprite):
    
    asset = ImageAsset("images/1122.png")
    
    
    def __init__(self, position):
        super().__init__(Bunny.asset, position)
        # register mouse events
        App.listenKeyEvent('keydown', 'w', w)
        App.listenKeyEvent('keydown', 'd', d)
        App.listenKeyEvent('keydown', 'a', a)
        self.scale = 0.12



    def step(self):
        global up
        global i
        global q
        global life
        
        if q and self.x < 1750:
            self.x += 50
            q -= 1
            
        if life and self.x > 50:
            self.x -= 50
            life -= 1
        if i:
            self.y += 10
            if self.y > 680:
                i =0
        if up and self.y > 0:
            self.y -= 10
        if self.y < 100:
            up -= 1
            i += 1

            

class Sun(Sprite):

    asset = ImageAsset("images/12.png")
    width = 80
    height = 76
    
    def __init__(self, position):
        super().__init__(Sun.asset, position)
        
    def step(self):
            self.x = 800
            self.y = 200

class Sun2(Sprite):

    asset = ImageAsset("images/12.png")
    width = 80
    height = 76
    
    def __init__(self, position):
        super().__init__(Sun2.asset, position)
        
    def step(self):
            self.x = 1300
            self.y = 200
            
class Sun3(Sprite):

    asset = ImageAsset("images/12.png")
    width = 80
    height = 76
    
    def __init__(self, position):
        super().__init__(Sun3.asset, position)
        
    def step(self):
            self.x = 300
            self.y = 200
            
class A(Sprite):

    asset = ImageAsset("images/1212.png")
    width = 80
    height = 76
    
    def __init__(self, position):
        super().__init__(A.asset, position)
        
    def step(self):
            self.x = 800
            self.y = 200
            
class A2(Sprite):

    asset = ImageAsset("images/1212.png")
    width = 80
    height = 76
    
    def __init__(self, position):
        super().__init__(A2.asset, position)
        
    def step(self):
            self.x = 1300
            self.y = 200

class A3(Sprite):

    asset = ImageAsset("images/1212.png")
    width = 80
    height = 76
    
    def __init__(self, position):
        super().__init__(A3.asset, position)
        
    def step(self):
            self.x = 300
            self.y = 200
            
class DemoApp(App):
    
    def __init__(self):
        super().__init__()
        self.sun = Sun((self.width/2, self.height/2))
        self.sun2 = Sun2((self.width/2, self.height/2))
        self.sun3 = Sun3((self.width/2, self.height/2))
        Bunny((900,700))
        self.A = A((self.width/2, self.height/2))
        self.A2 = A2((self.width/2, self.height/2))
        self.A3 = A3((self.width/2, self.height/2))

    def step(self):
        """
        Override step to perform action on each frame update
        """
        for bunny in self.spritelist:
            bunny.step()



# Create the app
app = DemoApp()  
# Run the app
app.run()

</script>
</body>
</html>

