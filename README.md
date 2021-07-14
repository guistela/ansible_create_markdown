# Ansible Jinja2 create markdown file

Ansible role that creates a markdown file based on a variable list of dicts

[![Build Status](https://app.travis-ci.com/guistela/ansible_create_markdown.svg?branch=main)](https://app.travis-ci.com/guistela/ansible_create_markdown)

# Role Variables

| Parameter | Choices/defaults | Comments |
| ------ | ----- | ----- |
| path_to | ./dir | Path to write the .md files |
| dict_list | a list of dictionaries | Ex.: [{'name': Dummy List 1,'rules':[{'name': 'Test1','id': '1', 'content': 'Content Test1'}]}] |

Dependencies
------------

There is no other role dependency.

Example Playbook
----------------

Check the syntax like the example, or use the playbook at playbooks folder.

    ---

    - hosts: localhost
      gather_facts: no
      vars:
        path_to: "../"
        dict_list:
          - name: Dummy List 1
            rules:
              - name: Test1
                id: 1
                content: "Content Test 1"
              - name: Test2
                id: 2
                content: "Content Test 2"
              - name: Test3
                id: 3
                content: "Content Test 3"
          - name: Dummy List 2
            rules:
              - name: Test1
                id: 1
                content: "Content Test 1"
              - name: Test2
                id: 2
                content: "Content Test 2"
              - name: Test3
                id: 3
                content: "Content Test 3"

      roles:
        - role: ../ansible_create_markdown



## Input and expected results

The following variable will produce the following markdown table in the file:

    dict_list:
        - name: Dummy List 1
          rules:
            - name: Test1
              id: 1
              content: "Content Test 1"
            - name: Test2
              id: 2
              content: "Content Test 2"
            - name: Test3
              id: 3
              content: "Content Test 3"
        - name: Dummy List 2
          rules:
            - name: Test1
              id: 1
              content: "Content Test 1"
            - name: Test2
              id: 2
              content: "Content Test 2"
            - name: Test3
              id: 3
              content: "Content Test 3"

##### File 1:

    # Name: Dummy List 1
    ## Count: 3  
    | name | id | content |
    | ------ | ----- | ----- |
    | Test1 | 1 | Content Test 1 |
    | Test2 | 2 | Content Test 2 |
    | Test3 | 3 | Content Test 3 |

##### File 2:
    # Name: Dummy List 2
    ## Count: 3  
    | name | id | content |
    | ------ | ----- | ----- |
    | Test1 | 1 | Content Test 1 |
    | Test2 | 2 | Content Test 2 |
    | Test3 | 3 | Content Test 3 |


The more contents you have in yout dict list, the more collumns/rows it will create in the .md file.
Be concearned to provide path and user with proper write privileges for the template module to create the files.

License
-------

MIT

Author Information
------------------

Guilherme Alves Stela <guistela@hotmail.com>
