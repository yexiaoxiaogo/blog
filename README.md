# jekyll-template
Template for Blog based on jekyll

# JDBC
```java
package io.github.yexiaoxiaogo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class HelloWorld {

	// JDBC 驱动名及数据库 URL
    static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";  
    static final String DB_URL = "jdbc:mysql://localhost:3306/yexiaoxiao";
 
    // 数据库的用户名与密码，需要根据自己的设置
    static final String USER = "root";
    static final String PASS = "123456";
    
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("hello world");
		Connection conn = null;
		Statement stmt =null;
		try {
			Class.forName(JDBC_DRIVER);
			
			conn = DriverManager.getConnection(DB_URL, USER, PASS);
			
			stmt = conn.createStatement();
			String sql;
			sql = "select id,name from person";
			ResultSet rs = stmt.executeQuery(sql);
			while (rs.next()){
				int id = rs.getInt("id");
				String name = rs.getString("name");
				
				System.out.println("id:"+ id);
				System.out.println("name:"+ name );
				System.out.println("\n");
				
			}
			rs.close();
			stmt.close();
			conn.close();
		} catch (Exception e) {
			// TODO: handle exception
		}
		

	}

}

```
# How-to
* Base Config: `_config.yml`

  ```
  title: your title
  email: your email
  description: >
    your description
  baseurl: "/jekyll-template" # the subpath of your site, e.g. /blog
  url: "https://zhoukekestar.github.io" # the base hostname & protocol for your site
  twitter_username: zhoukekestar
  github_username:  zhoukekestar

  # paging
  paginate: 10
  paginate_path: "/page:num/"

  # Build settings
  markdown: kramdown
  theme: minima
  kramdown:
  input: GFM
  ```

* Your blog header: `_includes/header.html`

  ```html
     <!-- your blog header -->
    <div class="trigger">
      <a class="page-link" href="/jekyll-template/search">Search</a>
      <a class="page-link" href="/jekyll-template/tags.html">Tags</a>
    </div>
  ```

* Your post comments: `_layouts/post.html`

  ```js
    // fetch your own comments
    fetch('https://api.github.com/repos/zhoukekestar/jekyll-template/issues/{{page.commentIssueId}}/comments', {
      headers: {
        Accept: "application/vnd.github.full+json"
      }
    }).then(function (response) {
      return response.json();
    }).then(function (body) {
      loadComments(body);
    })
  ```

* Your custom style: `css/main.scss`

  ```css
    .abc {
    /* your custom style */
    }
  ```
