# Publicações

Code:
```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  password="myroot",
  database="mt_public_db"
)

mycursor = mydb.cursor()

mycursor.execute("SELECT * FROM customer")

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
```

Publicações de Wilyan Fidelis, entusiasta em tecnologia com mais de 12 anos de experiência na área de automação industrial e programação. Veja mais na minha página [Willyan Fidelis](https://willyan.fidelisduino.com/).

## Python
<details>
  <summary>Click to expand!</summary>
  
  ### Python + MySQL
  [YouTube](https://github.com/willyan-fidelis/publication/blob/gh-pages/python-mysql.md)
</details>

## A collapsible section with markdown
<details>
  <summary>Click to expand!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>

## A collapsible section with markdown
<details>
  <summary>Click to expand!</summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>



### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/willyan-fidelis/publication/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
