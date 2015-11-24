#### 爬虫
-> 用到两个插件
    npm install superagent
    npm install cheerio (类似jquery)
https://cnodejs.org/topic/5203a71844e76d216a727d2e

eg:
   app.get('/', function(req, res){
    superagent
      .get('http://wiki.jikexueyuan.com/list/nodejs/#all-project')
      .end(function(err, doc){
        var $ = cheerio.load(doc.text),
          arr = [];
    
        $('.all-project  .sort li a').each(function(index, item){
          var _this = $(item);
          arr.push({
            title: _this.text()
          });
        });
        res.render('index', {
          data: arr
        })
      });
    
    })
