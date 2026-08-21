---
layout: default
title: プライバシーポリシー
---

# プライバシーポリシー

公開中のアプリケーションのプライバシーポリシーを掲載しています。

{% assign apps = site.apps | sort: "app_name" %}
{% if apps.size > 0 %}
{% for app in apps %}
- [{{ app.app_name }}]({{ app.url | relative_url }})（最終更新日: {{ app.last_updated }}）
{% endfor %}
{% else %}
現在、公開中のプライバシーポリシーはありません。
{% endif %}
