---
layout: page
permalink: /cv/
title: 简历
nav: true
nav_order: 3
description: 教育经历、工作经历、科研项目与教学
toc:
  sidebar: left
---

{% assign cv = site.data.cv.cv %}

**{{ cv.name }} · {{ cv.label }}**

{{ cv.summary }}

## 教育经历

<div class="table-responsive">
  <table class="table table-sm">
    <thead>
      <tr><th>时间</th><th>学校与院系</th><th>学位</th></tr>
    </thead>
    <tbody>
      {% for entry in cv.sections.Education %}
        <tr>
          <td class="text-nowrap">{{ entry.start_date | replace: '-', '.' }}–{{ entry.end_date | replace: '-', '.' }}</td>
          <td>{{ entry.institution }} · {{ entry.area }}</td>
          <td>{{ entry.studyType }}</td>
        </tr>
      {% endfor %}
    </tbody>
  </table>
</div>

## 工作经历

<div class="table-responsive">
  <table class="table table-sm">
    <thead>
      <tr><th>时间</th><th>机构</th><th>职务</th></tr>
    </thead>
    <tbody>
      {% for entry in cv.sections.Experience %}
        <tr>
          <td class="text-nowrap">
            {{ entry.start_date | replace: '-', '.' }}{% if entry.end_date %}–{{ entry.end_date | replace: '-', '.' }}{% else %} 起{% endif %}
          </td>
          <td>{{ entry.company }}</td>
          <td>{{ entry.position }}</td>
        </tr>
      {% endfor %}
    </tbody>
  </table>
</div>

2021年3月加入上海大学。以上任职信息依据2021年与2022年更新的官方教师资料整理。

## 代表性科研项目

{% for entry in cv.sections.Projects %}

- **{{ entry.name }}** · {{ entry.summary }}<br>
  {{ entry.start_date | replace: '-', '.' }}–{{ entry.end_date | replace: '-', '.' }}

{% endfor %}

## 讲授课程

{% for entry in cv.sections.Teaching %}

- {{ entry.bullet }}

{% endfor %}

## 联系方式

- 邮箱：[{{ cv.email }}](mailto:{{ cv.email }})
- 电话：[{{ cv.phone }}](tel:+862166136202)
- 地址：{{ cv.location }}
- 邮编：{{ cv.address.postalCode }}

代表性学术成果见[成果与论文]({{ '/publications/' | relative_url }})。

## 资料来源

{% for source in site.data.cv.sources %}

- [{{ source.title }}]({{ source.url }})，正文更新于 {{ source.updated | replace: '-', '.' }}{% if source.published %}，页面发布于 {{ source.published | replace: '-', '.' }}{% endif %}。

{% endfor %}
