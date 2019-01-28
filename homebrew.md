# Install specific version of package (https://goo.gl/a8ah47)
cd "$(brew --repo homebrew/core)"
git log Formula/ruby.rb
git co -b ruby-2.5.0 71fc82568a38bfa98b99fab7e85ef0e1464aec0c
brew unlink ruby
HOMEBREW_NO_AUTO_UPDATE=1 brew install ruby

# List and switch between different versions
brew list postgresql --versions
brew switch postgresql 9.6.5

# get info
brew info postgresql
