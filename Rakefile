## Rsync config ##

# Assumes that ssh is already set up on the server.
ssh_user      = "opattison@oliverpattison.org"
local_images  = "test" # typically called "_images"
local_site    = "_site" # typically called "_site"
remote_images = "webapps/static"
remote_site   = "webapps/development"
rsync_delete  = true

## "rake load" to load images in the local image directory to your server
desc "deploy Jekyll images to remote server via rsync"
task :load do
  system "rsync -avze --include='*.png' --include='*.jpg' ssh #{local_images}/ #{ssh_user}:{remote_images}/"
  puts "Deploying images via rsync"
end

## "rake deploy" to deploy _site to your server
desc "deploy Jekyll _site to remote server via rsync"
task :deploy do
  system "rsync -avze ssh #{"--delete" unless rsync_delete == false} #{local_site}/ #{ssh_user}:{remote_site}/"
  puts "Deploying _site via rsync"
end


# example: rsync -avze ssh test/ opattison@oliverpattison.org:webapps/static/