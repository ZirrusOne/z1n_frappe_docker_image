ARG FRAPPE_BRANCH=z1
FROM node:14-buster
ARG FRAPPE_BRANCH=version-13

COPY install_frappe.sh /install_frappe
COPY install_erpnext.sh /install_erpnext
COPY install_app.sh /install_app
COPY prepare_production.sh /prepare_production

# Install frappe
RUN /install_frappe ${FRAPPE_BRANCH} && \
  # Install erpnext
  /install_erpnext && \
  # Install required apps with following command
  # /install_app <app_name> <repo> <app_branch>
  /install_app install_manager https://github.com/ZirrusOne/install_manager develop && \
  # Cleanup for production
  /prepare_production

FROM frappe/erpnext-nginx:${FRAPPE_BRANCH}

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync

# Append list of installed to apps.txt
RUN echo -n "posawesome\nfrappe_s3_attachment\nmetabase_integration\nbookings\nbench_manager" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
