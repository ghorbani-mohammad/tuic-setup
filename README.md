First, install certbot on your server (Linux):

sudo apt update
sudo apt install certbot


Then request a certificate:

sudo certbot certonly --standalone -d your.domain.com

Certbot will save certificates here by default:

/etc/letsencrypt/live/your.domain.com/

Specifically:

    /etc/letsencrypt/live/your.domain.com/fullchain.pem

    /etc/letsencrypt/live/your.domain.com/privkey.pem

Mount in docker-compose like this:
volumes:
  - /etc/letsencrypt/live/your.domain.com/fullchain.pem:/etc/sing-box/cert.pem:ro
  - /etc/letsencrypt/live/your.domain.com/privkey.pem:/etc/sing-box/key.pem:ro
