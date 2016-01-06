FROM danigiri/docker-dnsmasq

COPY eureka-servers.conf /etc/dnsmasq.d/eureka-servers.conf
ENTRYPOINT ["/usr/sbin/dnsmasq", "--keep-in-foreground", "-C"]
CMD ["/etc/dnsmasq.conf"]
