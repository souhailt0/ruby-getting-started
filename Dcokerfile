# Use the appropriate base image
FROM ruby:3.1

# Set the NIXPACKS_PATH to include the correct Ruby versions
ENV NIXPACKS_PATH="/usr/local/rvm/rubies/ruby-3.1/bin:/usr/local/rvm/gems/ruby-3.1/bin:/usr/local/rvm/gems/ruby-3.1@global/bin:$NIXPACKS_PATH"

# Install dependencies
RUN apt-get update && apt-get install -y \
  build-essential \
  libpq-dev \
  nodejs

# Set the working directory
WORKDIR /app

# Copy the Gemfile and Gemfile.lock
COPY Gemfile /app/Gemfile
COPY Gemfile.lock /app/Gemfile.lock

# Install the Ruby gems
RUN bundle install

# Copy the rest of the app
COPY . /app

# Expose the port that the app runs on
EXPOSE 3000

# Start the Rails server
CMD ["rails", "server", "-b", "0.0.0.0"]
