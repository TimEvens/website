---
title: Documentation
image: background_image_01.png

#
# .Params.menu can be accessed in the template/layouts
#
#  The side bar navigation will be auto generated based on this variable
#  Format:
#     Array of objects:
#       {
#         href:     Relative or absolute URL path OR if this is a submenu
#                   item, then use #<menu name>, no spaces. This will be the menu id
#         label:    String label used for the menu item,
#         parent:   For now you need to define the parent href value.  The parent is the
#                   href for the submenu or if at root it should be "#sidebar"
#         icon:     Optional font awesome class, such as fa-code,
#
#         items:    Optional array of submenu objects
#       }
#
menu:
    - href: '#getting_started'
      label: Getting Started
      parent: '#sidebar'
      icon: fa-cloud-download

      items:
        - href: quick_start
          label: Quick Start
          parent: '#getting_started'
        - href: requirements
          label: Requirements
          parent: '#getting_started'
        - href: '#install_sub_menu'
          label: Docker Install
          parent: '#getting_started'
          items:
            - href: install
              label: Install Docker
              parent: '#install_sub_menu'
            - href: install_aio
              label: All-In-One Docker
              parent: '#install_sub_menu'
            - href: install_ui
              label: UI Docker
              parent: '#install_sub_menu'
            - href: install_collector
              label: Collector Docker
              parent: '#install_sub_menu'
            - href: install_kafka
              label: Kafka Docker
              parent: #install_sub_menu'
            - href: install_mysql
              label: MySQL Docker
              parent: '#install_sub_menu'
            - href: aio_ipv6
              label: AIO IPv6 Configuration
              parent: '#install_sub_menu'
        - href: install_ubuntu
          label: Ubuntu Install
          parent: '#getting_started'
        - href: build
          label: Building Source
          parent: '#getting_started'
        - href: db_geo_coding
          label: Custom DB Geo-Coding          
          parent: '#getting_started'

    - href: '#usecases'
      label: Use Cases
      parent: '#sidebar'
      icon: fa-user
      items:

    - href: '#configs'
      label: Configuration
      parent: '#sidebar'
      icon: fa-cog
      items:
        - href: router_config
          label: Router Configs
        - href: router_bgpls_config
          label: Router BGP-LS Config

    - href: '#develop_api'
      label: SDK's and API's
      parent: '#sidebar'
      icon: fa-code
      items:
        - href: message_bus_api
          label: Message Bus API
          
        - href: db_schema
          label: Database Schema

    - href: '#develop_int'
      label: Developer Integration
      parent: '#sidebar'
      icon: fa-code
      items:
        - href: consumer_developer_integration
          label: Consumer Integration
        - href: logstash
          label: Using Logstash

    - href: '#troubleshooting'
      label: Troubleshooting
      parent: '#sidebar'
      icon: fa-child
      items:
---

The main architectural components of the SNAS framework are:

A high speed, low foot print collector, a high performance message bus, consumer applications, database, APIs and user applications

<!--more-->

## Flow

SNAS streams data from the network using a high performance collector.
    The collector produces the parsed (and raw) BMP data to Kafka message bus
    using a customizable topic structure.

![](/img/arch1.svg)

Consumer applications can access to data using regular Kafka APIs.
    One of these consumers is called mysql-consumer and is responsible for
    storing the data in a mysql/mariadb database. Applications can access
    the data in the database either using the RESTful API or natively.

## Architecture Diagram

![](/img/arch2-1.svg)