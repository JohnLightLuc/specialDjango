# Django

## Context processors

1- Créer la fichier context_processor.py dans le projet
    
    #context_processor.py
    def getdata(self):
        ...
        return data
        
 2- Configuraton
 
    //setting.py
    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [os.path.join(BASE_DIR, 'templates')],
            'APP_DIRS': True,
            'OPTIONS': {
                'context_processors': [
                    ...

                    'context_processor.getdata',

                ],
            },
        },
    ]
    
  3 - VIEWS.PY
  
    ...
    from django.template import RequestContext
    
    def context(request):
        return render(request, 'page.html', context=RequestContext(request))
        
        
4 - Affichage dans page.html


## Field Slug (models.py)

1-Import 

    ...
    from django.utils.text import slugify
    import hashlib
  
2- Class

    class Article(models.Model):
        titre = models.CharField(max_length =255)
        titre_slug = models.SlugField(editable=False, null=True, max_length=255)
        ....
        
        def save(self, *args, **kwargs):
            super(Article, self).save(*args, **kwargs)
            encoded_id =hasblib.md5(str(self.id).encode())
            self.titre_slug = slugify(self.titre +' '+str(encoded_id.hexdigest()))
            super(Article, self).save( *args, **kwargs)
            
            
       ex: lorem-ipsum-dolor-sit-amet-e4da3b7fbbce2345d7772b0674a318d5
            
           
                  
        
    
    
    
    
    
    
    
    
    



    
  
  
  
