# Superfic Social Network

> In the backend, one external library [PHP dotenv](https://github.com/vlucas/phpdotenv) is used to load environment variables.

## Prerequisites

-   [Git](https://git-scm.com/)
-   [Docker](https://www.docker.com/)
-   [Composer](https://getcomposer.org/)
-   [Yarn](https://yarnpkg.com/)
-   [Curl](https://curl.haxx.se/)

## Local development setup with Docker Compose

1.  Clone the repository:

        git clone --recursive git@github.com:lyonsun/superfic-social-network.git

2.  Rename `.env.sample` to `.env`:

        cd superfic-backend
        mv .env.sample .env

3.  Provide your own secret credentials in `.env`.

4.  Install backend dependencies:

        composer install

5.  Rename `.env.local.sample` to `.env.local`:

        cd ../superfic-frontend
        mv .env.local.sample .env.local

6.  Change credentials to your own backend URL

7.  Start up the development servers in docker containers:

        cd ..
        docker-compose --env-file ./superfic-backend/.env up

    -   or if you want to rebuild the containers at some point:

              docker-compose --env-file ./superfic-backend/.env up --build

## Backend

### Build the database

    curl -X GET "http://localhost:8080/index.php/ping"

### Endpoints

-   http://localhost:8080/index.php/get_all_posts
-   http://localhost:8080/index.php/get_posts?page=1&count=1
-   http://localhost:8080/index.php/get_posts_count?user_id=1
-   http://localhost:8080/index.php/get_posts_count?user_id=1&month=1
-   http://localhost:8080/index.php/get_monthly_posts_count?user_id=1
-   http://localhost:8080/index.php/get_average_characters_count?user_id=1
-   http://localhost:8080/index.php/get_longest_post?user_id=1

## Frontend

### Hot reloading in development

To hot reload the frontend in development, follow these setup steps instead:

-   Stop all currently active development servers in docker containers:

        cd ..
        docker-compose --env-file ./superfic-backend/.env down

-   Open `docker-compose.yml` and comment out the `frontend` container.
-   Rebuild and run the development servers in docker containers:

        cd ..
        docker-compose --env-file ./superfic-backend/.env up --build

-   Open another terminal and start the frontend in development mode:

        cd superfic-social-network/superfic-frontend
        yarn dev

-   Rebuild the database:

        curl -X GET "http://localhost:8080/index.php/ping"

### View the website

Visit http://localhost:3000/ in your browser.

## Credits

-   [PHP dotenv](https://github.com/vlucas/phpdotenv)
-   [Next.js](https://nextjs.org/)
-   [Tailwind CSS](https://tailwindcss.com/)
-   [React Paginate](https://github.com/AdeleD/react-paginate)
-   [Heroicons](https://heroicons.com/)
-   Illustration by <a href="https://icons8.com/illustrations/author/zD2oqC8lLBBA">Icons 8</a> from <a href="https://icons8.com/illustrations">Ouch!</a>
