ARG  FROM_IMAGE=xoelabs/dockery-odoo
FROM ${FROM_IMAGE}

USER root

# get marabunta as the odoo migration controller library of choice
RUN pip install git+https://github.com/xoe-labs/marabunta#egg=marabunta

# You can configure marabunata either by environment variables
# or by config flags (which override env variables)
# Some arbitraty defaults
ENV MARABUNTA_ODOO_CMD ${ODOO_BASEPATH}/odoo-bin
ENV MARABUNTA_MIGRATION_FILE ${ODOO_BASEPATH}/.marabunta.yml

COPY entrypoint* /
COPY entrypoint.d/* /entrypoint.d/

USER odoo

ENTRYPOINT ["/entrypoint-migrator.sh"]
CMD ["--help"]
