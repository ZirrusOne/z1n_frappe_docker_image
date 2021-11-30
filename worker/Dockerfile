ARG FRAPPE_BRANCH=v13.15.1
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

RUN install_app install_manager https://github.com/ZirrusOne/install_manager develop && \
  bench build
