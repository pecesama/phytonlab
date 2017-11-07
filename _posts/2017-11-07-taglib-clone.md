---
layout: post
title:  "Taglib clone"
date:   2017-11-07 13:09:02 -0600
categories: python
---

A Python clone of the Homebrew's Taglib.

![Screenshot]({{ "/assets/taglib.jpg" | absolute_url }})

{% highlight python %}
import os
import taglib
import PIL.Image

import base64

from mutagen import File
from wsgiref.simple_server import make_server
from pyramid.config import Configurator
from pyramid.response import Response
from pyramid.response import FileResponse
from pyramid.view import view_config
from io import BytesIO

tagList  = ['TITLE','ARTIST','ALBUMARTIST']

def getAllFilesAsList(root,exts):
    l =list()    
    for path, subdirs, files in os.walk(root):
        for name in files:
            l.append(os.path.join(path,name)) if name[name.rindex('.'):] in exts else None
    return l
"""



"""
def getEmbeddedImage(l,defIimage='static/pixel.gif', h='100px',w='100px'):
    try:
        b = File(l).tags['APIC:'].data
        img = PIL.Image.open(BytesIO(b))

        if (img.format =='JPEG'):
            return '<img alt="Embedded Image" src="data:image/jpeg;base64,'+base64.b64encode(b).decode('utf-8')+'" width="'+(w)+'" height="'+(h)+'"  />'
        else: 
            return '<img alt="Embedded Image" src="data:image/png;base64,'+base64.b64encode(b).decode('utf-8')+'" width="'+(w)+'" height="'+(h)+'"  />'
            
            
    except:
        
        return '<img alt="Embedded Image" src="'+defIimage+'" width="'+(w)+'" height="'+(h)+'"  />'

    """



    """
def getRowData(l):
    s = '<tr><td>'+getEmbeddedImage(l,defIimage='static/not_found.gif')+'</td>'
    d = taglib.File(l).tags
    for k in tagList:
        s=s+'<td>'+str(d.get(k, 'Null'))+'</td>'
    s=s+'<td>'+l[l.rindex('/'):]+'</td>'
    
    s = s+'</tr>'
    return s

"""

"""

def mp3ListRequest(request):
    print()
    print(type(request))
    print('Incoming request, hello_world')
    s = ''
    for l in getAllFilesAsList('music_directory_path',['.mp3']):
        s = s + getRowData(l)
    response = '<html><head><title>Phyton Labs</title><link rel="stylesheet" type="text/css" href="static/tablecss.css"></head><body><h1>' +'.........'+ '</h1><table>' +s+'</table></body><html>'
    return Response(response)

if _name_ == '_main_':


    os.system('clear')
    with Configurator() as config:
        config.add_view(mp3ListRequest)
        config.add_route('mp3list', '/mp3list')
        config.add_static_view('static', 'static', cache_max_age=3600)
        config.add_view(mp3ListRequest, route_name='mp3list')
        config.scan('_main_')
        app = config.make_wsgi_app()
         
    server = make_server('0.0.0.0', 6543, app)
    print('Starting server')
    server.serve_forever()
{% endhighlight %}