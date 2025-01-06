---
title: "Changelog"
layout: "layouts/changelog.html"
changelog:
    - date: "2024-11-01"
      title: "v5.9.0"
      items:
        - "Fix: the caching issue related to checking the plugin version."
        - "Fix: Addressed server inaccessibility issue caused by metabox behavior changes in version 5.9.11, allowing admin users to access `dvi_app_server` post types by overriding capability checks."
        - "New: support for Ubuntu 24.04."
        - "New: Added `is_ubuntu_24_4` function to detect if the system is running Ubuntu 24.04."
        - "New: Added `restart_ssh_service` function to restart the correct SSH service based on Ubuntu version (either ssh for Ubuntu 24.04 or sshd for other versions)."
        - "Enhancement: Replaced direct usage of systemctl restart sshd with the new restart_ssh_service function for better flexibility and compatibility across different Ubuntu versions."
        - "Fix: Removed the conditional check that prevented the installation of non-Nginx web servers on Ubuntu 24.04, as OpenLiteSpeed (OLS) now officially supports Ubuntu 24.04."
        - "Update: MB Admin Columns plugin version to 1.7.5"
        - "Update: Meta Box Conditional Logic plugin version to 1.6.24"
        - "Update: Meta Box Include Exclude plugin version to 1.1.1"
        - "Update: Meta Box Show Hide plugin version to 1.3.1"
        - "Update: Meta Box Tooltip plugin version to 1.1.8"
        - "Update: Meta Box Tabs plugin version to 1.1.18"
        - "Update: Meta Box Group plugin version to 1.4.2"
        - "Update: Meta Box Columns plugin version to 1.2.16"
        - "Update: MB User Meta plugin version to 1.2.10"
        - "Update: MB Term Meta plugin version to 1.2.11"
        - "Update: MB Settings Page plugin version to 2.1.13"
        - "Update: MB Custom Table plugin version to 2.1.13"
    - date: "2024-10-02"
      title: "v5.8.6"
      items:
        - "Fix: Resolved the issue with 'One Click Login' generation. The problem occurred when the login link was not sent."
        - "Enhancement: The WordPress version fetching mechanism was improved. Previously, it relied on a manually updated array; this has been upgraded to an API that automatically fetches the latest versions."
        - "New: Added `apply_filters('dvi_allowed_min_wp_version', $min_version);` to allow users to specify the minimum allowed WordPress version, with a default set to 6.1.4."
        - "New: Introduced a new setting (option) named 'Min Allowed WP Versions' in the DVI settings to enable users to set the minimum allowed WordPress version."

    - date: "2024-08-03"
      title: "v5.8.5"
      items:
        - "Fix: compatibility issue with MariaDB 10.4+ dump files."
        - "Tweak: WPAPP - Updated WP version list to latest versions."

    - date: "2024-07-25"
      title: "v5.8.4"
      items:
        - "New: Added an update message inside the plugin in WordPress to receive the latest versions of the plugin."
        - "Fix: Prevent server restart nginx when creating a site."
        - "Fix: Prevent server restart nginx when changing the domain."
        - "Tweak: WPAPP - Updated WP version list to latest versions."

---
