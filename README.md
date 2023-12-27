# rails-docker-niko

terminal名前変更
# vim ~/.zshrc の下の方に貼り付け
export PS1="%1~ %# " 


https://github.com/kiyodori/rails-docker-niko.git
kyt 全部変換　niko

00:53:34　アプリを作成・実行しよう (  

 • 【Docker超入門 #5】アプリを作成・実行しよう  )



 405  cd rails-docker-niko
  406  cd sample
  407  cd 05_CREATE_APP
 
  408  history
   
  
  421  docker image build -t sample/webrick:latest .
  422  docker container run -p 8000:8000 --name webrick sample/webrick:latest

  http://localhost:8000/
  にて完成

    195  docker container logs webrick
  196  docker container exec webrick ruby -v
  197  docker system prune -a


01:15:04　Dockerfileを作ろう (  

 • 【Docker超入門 #6】Dockerfileを作成しよう  )

440  cd 06_DOCKERFILE
  441  docker image -t sample/sinatra:latest .
  442  docker image build -t sample/sinatra:latest .
  444  docker container run -it -p 4567:4567 --name sinatra -v ${PWD}/src:/var/www sample/sinatra:latest

root@c6cdd65164ac:/var/www# history
    1  ls
    2  bundle config --local set path 'vender/bundle'
    3  bundle install
 
    5  bundle exec ruby app.rb
    6  history

  445  docker container rm sinatra
  447  docker image build -t sample/sinatra:latest .
  448  docker container run -p 4567:4567 --name sinatra -v ${PWD}/src:/var/www sample/sinatra:latest

  http://localhost:4567/
  完成


  01:36:37　Docker ComposeでRailsを構築しよう (  

 • 【Docker超入門 #7】Docker ComposeでRailsを構築しよう  )

456  cd rails-docker-niko2
 
  462  docker-compose run web rails new . --force --database=mysql
  463  docker-compose build
  464  docker-compose run web rails db:create
  465  docker-compose up
  
