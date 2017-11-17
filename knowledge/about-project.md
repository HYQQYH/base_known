### 项目相关

 1. flask中,从外部传参给函数内部:
 

    >from flask import app
    app.config['engine'] = KGQAEngine(CONFIG_PATH) 
    \#在函数内部使用app.config['engine']可获取从外部传入的参数,此处是KGQAEngine(CONFIG_PATH) 
    存在函数:
    def _query(q, verbose=False): 
	    res = app.config['engine'].answer(q)
    

 2. 

