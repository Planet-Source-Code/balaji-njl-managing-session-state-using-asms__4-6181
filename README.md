<div align="center">

## Managing Session State using aSMS


</div>

### Description

Managing Session and Application Variables across web servers in a web farm.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Balaji NJL](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/balaji-njl.md)
**Level**          |Advanced
**User Rating**    |3.8 (15 globes from 4 users)
**Compatibility**  |ASP \(Active Server Pages\)
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__4-7.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/balaji-njl-managing-session-state-using-asms__4-6181/archive/master.zip)





### Source Code


<table border="0" cellPadding="0" cellSpacing="0">
 <tbody>
  <tr>
   <td>&nbsp;</td>
  </tr>
  <tr>
   <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="title"><b>Managing
    Session State using aSMS<br>
    </b></span></font></td>
  </tr>
  <tr>
   <td>&nbsp;</td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Introduction">Introduction</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Using Cookies to Maintain State">Using
    Cookies to Maintain State</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Managing Session State Across Multiple Web Servers">Managing
    Session State Across Multiple Web Servers</a><a><br>
    </a></b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Building Web Applications with no state">Building
    Web Applications with no &quot;state&quot;</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Storing Session information completely on the User Machine">Storing
    Session information completely on the User Machine</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Intelligent Session-Aware Routing of Requests">Intelligent
    Session-Aware Routing of Requests</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Centralized State Management">Centralized
    State Management</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td vAlign="top" width="18"><img alt border="0" height="10" hspace="0" src="http://domaindlx.com/asms/img/b-bk.gif" width="10"></td>
   <td vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><b><a href="#Conclusion">Conclusion</a><br>
    </b></span></font></td>
  </tr>
  <tr>
   <td>&nbsp;</td>
  </tr>
  <tr>
   <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
    <div class="title">
     <a name="Introduction">Introduction</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
    </div>
   </td>
  </tr>
  <tr>
   <td colSpan="2" vAlign="top">
    <p><font face="verdana, arial, helvetica" size="2"><span class="eight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Millions
    of users all over the globe access and surf the Internet with a Web
    Browser. The Web browsers offer them functionality to connect to any
    site on the internet and view Web pages. How this happens, remain
    hidden. It is Hypertext Transport Protocol that makes it all possible.
    HTTP is a stateless protocol that defines how a Web browser communicates
    with a Web server. Once the user has started browsing a site, user sees
    related pages in a logical sequence. What actually happens is - every
    time the user clicks for a page, it goes to Web Server as a new HTTP
    request. Every request is separate and distinct. Web server cannot
    distinguish between the users or user requests for a web page. This
    means, all the web page requests of the user are distinct and do not
    depend upon the previous web page. Thousands of request come to the Web
    server every second. Maintaining user information for each and every
    user and sharing these information across web pages is known as
    'maintaining state'.&nbsp;</span></font></p>
   </td>
  </tr>
  <tr>
   <td>&nbsp;</td>
  </tr>
  <tr>
   <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
    <div class="title">
     <a name="Using Cookies to Maintain State">Using Cookies to Maintain
     State</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
    </div>
   </td>
  </tr>
  <tr>
   <td>
    <div>
    </div>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">
      <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; A cookie is a token of
      information stored on the user's machine. This piece of information
      comes from the web server, when the user makes an HTTP request. As
      the user surfs the web site , s/he may be getting many cookies, each
      specific to a Web site. When the user visits the site again, the
      browser packages it and sends this piece of information (cookies) to
      the web server along with the HTTP request. These cookies contain
      some information about the user, which the server needs to know.
      This is required in order to give this user a personalized
      experience of the web site. The contents of the cookies are read
      and/or more information added by the web server before it is
      returned back to the user.</p>
      <p>Every cookie is destroyed, either at the end of the browser
      session(or state) or if specified, on that expiration date set to
      sometime in the future. Till that time it is stored on the user's
      disk.</p>
      <p>A cookie stores a unique identifier, which is used by the web
      server to extract additional information of the user. This cookie
      acts as the key to his private and sensitive information. It is more
      secure to store this on user's machine than on the server in the
      database. And the web server determines whether this user is a new
      user or returning user, by the cookie. When an HTTP request carries
      no cookie or a cookie with no identifier, this user is a new user
      and a new identifier has to be generated for this user. This is then
      written to the cookie and sent back to the user machine. User
      information on the server is also updated. Otherwise, the existing
      identifier in the cookie is used to extract user information.</p>
      <p>Now lets understand what a &quot;User Session&quot; is - This is
      the duration starting from the time the user visits the first page
      of web site and ends when he/she leaves the site, by switching over
      to another site or by closing his/her browser. This end of the
      session can also be forced by a command/application running on the
      web server. And the set of information, which is related to user and
      to this session, is the &quot;session state&quot;. This information
      is maintained using cookies.</p>
      Microsoft® Internet Information Server (IIS), the Microsoft Web
      Server, has a built-in Session Object which maintains sessions using
      the cookies as described above.</span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" style="LEFT: 0px; TOP: 1px" width="30" height="22">
      <div class="title">
       <a name="Managing Session State Across Multiple Web Servers">Managing
       Session State Across Multiple Web Servers</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      For large and more popular sites, two or more servers are used to
      host the site. This is called a Web Farm. This arrangement becomes a
      necessity when the site expects a lot of hits. For better
      performance and efficiency, HTTP requests are usually handled in
      round robin fashion across each server.
      <p>As mentioned before, IIS session object handles session state
      well on a single web server, but it is a challenge to use this in a
      web farm. This is due to the fact that it tracks user session
      information only in the web server, to which the user's HTTP request
      goes. When subsequent requests by the same user is routed to another
      web server in a web farm, this server is not aware of any piece of
      information provided by the user during previous requests, as these
      were routed to different web server. This situation is exceptionally
      critical when a small single-server site already using Session
      Object is to be upgraded to a web farm.</p>
      <p>There are alternatives for this problem, as discussed below:</p>
      </span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
      <div class="title">
       <a name="Building Web Applications with no state">Building Web
       Applications with no &quot;state&quot;</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      These applications use the very native nature of a web application
      and are highly scalable. In such applications, every HTTP request is
      considered to be distinct with no relation to previous requests( no
      state). But not all application fit into this model.</span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
      <div class="title">
       <a name="Storing Session information completely on the User Machine">Storing
       Session information completely on the User Machine</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      This will allow all user specific session information to be stored
      on the user machine. This is preferable from web server's
      perspective as it requires no storage space on web server to store
      user information. But has some limitations - storage space on user
      and security. Browsers support cookies(stored on user machine), of
      size around 4KBs. And security is another concern with cookies. As
      cookie travels along with every HTTP request, it is all the more
      vulnerable to fall in sniffer's trap.</span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
      <div class="title">
       <a name="Intelligent Session-Aware Routing of Requests">Intelligent
       Session-Aware Routing of Requests </a><a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      This is routing of all the requests of a session to the same web
      server, so that there is no question of maintaining session
      information across web servers. This approach works perfectly in
      single-server model as well as in a web farm. It is easy for a small
      single-server based site to grow into a multiple server one with
      this approach. But it has its own disadvantages. It&#8217;s difficult to
      consolidate user information across web server. Also, load balancing
      cannot be done very efficiently, as the subsequent requests of
      sessions started on one web server, will be routed to the same web
      server, while the other server may remain idle for long time. The
      first server being very busy will give slow responses and low
      performance.
      <p>&nbsp;</p>
      <p>This approach can be implemented through software or hardware
      techniques.<br>
      </p>
      </span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top">
      <div class="title">
       Intelligent Session-Aware Routing through Software- <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight"><br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Many types of server level
      applications can be written to accomplish session aware routing
      through software. One of them is described here.A Web farm consists
      of two or more servers that host and serves a common logical-DNS
      host name. Load balancing is done in a DNS round-robin fashion. For
      example, the DNS name home.zzz.com might be resolved to one of three
      different Web servers named home1.zzz.com, home2.zzz.com and
      home3.zzz.com.<br>
      <br>
      On HTTP request to one of the physical hosts, the server(or
      application running on server) redirects the request to the server
      with the lowest CPU utilization(the most idle server) using its
      physical host name (home3.zzz.com) rather than the logical host name
      of the Web farm (home.zzz.com). All subsequent requests in that
      session to relative URLs by that browser are handled by the same
      physical server (home3.zzz.com). As long as all hyperlinks reference
      relative URLs, the browser will assume the URL is on the same host,
      and will submit the request to that host for processing.<br>
      <br>
      This technique requires a site to use only relative-URL hyperlinks
      within its documents.<br>
      </span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top">
      <div class="title">
       Intelligent Session-Aware Routing through Hardware- <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">&nbsp;&nbsp;&nbsp;&nbsp;<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Intelligent routers (such as <a href="http://www.cisco.com/warp/public/cc/cisco/mkt/scale/locald/index.shtml">Cisco's
      LocalDirector</a> ) allow a group of servers in a web farm to appear
      as one virtual server. The IP address of the virtual server is
      registered with the DNS server, while the IP addresses of the
      servers themselves remain undisclosed. When this virtual server
      receives requests, the router distributes the requests to one of
      them. The entire group of servers thus appears to the user as a
      single server. For more information, contact Cisco directly, or
      visit the <a href="http://www.cisco.com/warp/public/cc/cisco/mkt/scale/locald/index.shtml">LocalDirector</a>
      site.</span></font></td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
      <div class="title">
       <a name="Centralized State Management">Centralized State
       Management</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">
      <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This is a true server-side-only
      solution to the session-state problem. To assign the task of session
      management to a central server accessible by all the other servers
      in the farm. There can be different ways to implement this model.</p>
      <p>One way can be to maintain session state information in a
      relational database server like Microsoft® SQL Server.</p>
      <p>Other way is using asp Session Management Server (aSMS). Instead
      of using a database, the aSMS uses the LDAP on the central server.</span></font></p>
     </td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top">
      <div class="title">
       asp Session Management Server
      </div>
      <div class="title">
       &nbsp;
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">
      <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aSMS uses LDAP to maintain state
      information in a Web farm. LDAP can be a centralized server in the
      Web farm. All the webservers (aSMS) are mapped to this centralized
      LDAP server. aSMS uses LDAP because LDAP is optimized for fast
      single read and write operation. LDAP may internally use a database
      to store the data.<br>
      <br>
      aSMS uses ADSI to communicate to the centralized LDAP server. ADSI
      will work with any directory service that offers an ADSI provider
      like LDAP. The LDAP provider works with any LDAP version 2 or
      version 3 directory. This means aSMS can use any LDAP servers on any
      OS theoretically. Currently aSMS has been tested on Microsoft LDAP
      server i.e. Microsoft Site Server 3.0. Microsoft Site Server 3.0
      installs LDAP and uses MS Access or SQL server as internal database.<br>
      <br>
      The aSMS uniquely identifies each user by automatically generating a
      globally unique identifier (GUID) for all users on their initial
      visit. The GUID is then used as a key for storing information in the
      LDAP. The GUID is returned to the client as part of the HTTP
      response, and is stored as a cookie on the client's machine. When
      the user returns to the same host, the browser automatically
      packages the cookie in the header of the HTTP request. The aSMS on
      the server checks for the existence of the cookie in the HTTP
      request to determine if the request is from a new or existing user.
      If the cookie is present, the request is from an existing user, and
      the object is initialized with the information specific to that
      user. If the cookie is missing, then aSMS assumes the request is
      from a new user, and a new GUID is generated. In all cases, the
      process of identifying the user and initializing the LDAP is hidden
      from the ASP developer. The aSMS handles the mapping internally.<br>
      <br>
      aSMS acts as a kind of broker in between web servers and LDAP
      server. aSMS also provides a wrapper around ADSI so that the LDAP
      server need not be installed on each and every webserver or in any
      webserver. LDAP server can be a centralized stand-alone machine and
      all the aSMS (webservers) can be mapped to this LDAP server.</span></font></p>
     </td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top">
      <div class="title">
       Using aSMS
      </div>
      <div class="title">
       &nbsp;
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">
      <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; In IIS Session Starts
      automatically when the users hit the first web page usually
      default.asp. In aSMS developers have the flexibility of starting the
      session in any page from where they want to use session variables.<br>
      <br>
      aSMS does not use IIS&#8217;s Session management. It uses it&#8217;s
      internal session management tool. Developers can disable the IIS
      Session State from MMC there by conserving lot of resources.<br>
      <br>
      <b>How to Start a Session</b><br>
      <br>
      To start a Session, a developer must first create an instance of the
      aSMS Session object. This is done by calling the Server.CreateObject()
      method, and passing it Session.Management as the ProgId:<br>
      <br>
      &lt; % Set objSession = Server.CreateObject(&quot;Session.Management&quot;)
      % &gt;<br>
      <br>
      Once created, session can be started using the SessionStart() method<br>
      <br>
      &lt; % objSession.SessionStart() % &gt;<br>
      <br>
      <b>How to End a Session</b><br>
      <br>
      To end a session SessionEnd() method can be used.<br>
      <br>
      &lt; % objSession.SessionEnd() % &gt;<br>
      <br>
      <b>How to Check Session</b><br>
      <br>
      aSMS allows the developers to check for the session in any page by
      just calling CheckSession() method. This method checks whether the
      user is still in session or timed out .<br>
      <br>
      &lt; % objSession.CheckSession() % &gt;<br>
      <br>
      As a general rule of thumb this method has to be called in all the
      pages where session variables are used. This gives more flexibility
      to the developers and also resources can be conserved in other pages
      where session variables are not used.<br>
      <br>
      <b>How to Assign Session Variables <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a></b><br>
      <br>
      Session variables can be assigned by using SetSession() method.
      SetSession() method requires two arguments, one is name of the
      session variable and other is the value.<br>
      <br>
      &lt; % objSession.SetSession cstr(strName), cstr(strValue) % &gt;<br>
      <br>
      In aSMS standard edition, developers can use the predefined variable
      names in LDAP. LDAP contains more than 150 variable names defined
      with data types as int, float, date, image, array etc. Developers
      can select the appropriate variable names and use them.<br>
      <br>
      For e.g. some of the commonly used Session variable names and their
      corresponding LDAP variable names with their type<br>
      <br>
      FirstName &#8211; givenName (string)<br>
      LastName &#8211; sn (string)<br>
      EmailAddress &#8211; mail (string)<br>
      Password &#8211; userPassword (string)<br>
      State &#8211; accountStatus (int)<br>
      <br>
      For the complete listing of LDAP variable names <a href="http://domaindlx.com/asms/ldapvariables.asp">Click
      Here</a>.<br>
      <br>
      Session variables can be assigned as:<br>
      <br>
      &lt; %<br>
      Set objSession = Server.CreateObject(&quot;Session.Management&quot;)<br>
      <br>
      objSession.CheckSession()<br>
      <br>
      objSession.SetSession &quot;givenname&quot;, &#8220;John&#8221;<br>
      <br>
      objSession.SetSession &quot;sn&quot;, &#8220;Anderson&#8221;<br>
      <br>
      objSession.SetSession &quot;mail&quot;, &#8220;John@Anderson.com&#8221;<br>
      <br>
      objSession.SetSession &quot;userPassword&quot;, &#8220;password&#8221;<br>
      <br>
      objSession.SetSession &quot;accountStatus &quot;, &#8220;1&#8221;<br>
      <br>
      Set objSession = nothing<br>
      % &gt;<br>
      <br>
      <b>How to retrieve the Session Variables <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a></b><br>
      <br>
      Session variables can be retrieved by using GetSession() method.
      GetSession() requires the session variable name passed as argument.<br>
      <br>
      &lt; % objSession.GetSession(cstr(strName)) % &gt;<br>
      <br>
      &lt; %<br>
      Dim strFirstName, strLastName, strEmailAddress<br>
      Dim strPassword, intStatus<br>
      <br>
      Set objSession = Server.CreateObject(&quot;Session.Management&quot;)<br>
      <br>
      objSession.CheckSession()<br>
      <br>
      strFirstName = objSession.GetSession (&quot;givenname&quot;)<br>
      <br>
      strLastName = objSession.GetSession (&quot;sn&quot;)<br>
      <br>
      strEmaiAddress = objSession.GetSession (&quot;mail&quot;)<br>
      <br>
      strPassword = objSession.GetSession (&quot;userPassword&quot;)<br>
      <br>
      intStatus = objSession.GetSession (&quot;accountStatus &quot;)<br>
      <br>
      Set objSession = nothing<br>
      % &gt;<br>
      <br>
      By this approach the session variables can be easily shared across
      different webservers in the Web farm without losing the data. As
      mentioned earlier LDAP is optimized for fast single read and write
      operations, so storing the session variables in LDAP wont harm the
      performance of the web server.<br>
      <br>
      <b>Migrating a current web site to use aSMS</b><br>
      <br>
      For Migrating a current web site to aSMS check <a href="http://domaindlx.com/asms/deployment.asp">Migration/Deployment
      Page</a>.</span></font></p>
     </td>
    </tr>
    <tr>
     <td>&nbsp;</td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img align="left" alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/fldr2.gif" width="30" height="22">
      <div class="title">
       <a name="Conclusion">Conclusion</a> <a href="#"><img border="0" src="http://domaindlx.com/asms/img/arrow_green.gif" width="16" height="13"></a>
      </div>
     </td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><font face="verdana, arial, helvetica" size="2"><span class="eight">
      <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; In this paper, we've discussed
      state management in a Web farm where two or more servers are used to
      host a single site. We've looked at several possible approaches to
      managing session state, including building stateless applications,
      storing session state on the client, using session-aware
      load-balancing, and storing session state on a central computer
      using asp Session Management Server..<br>
      <br>
      <br>
      <br>
      <b>Disclaimer</b><br>
      <br>
      The names of companies, products, people, characters, and/or data
      mentioned herein are fictitious and are in no way intended to
      represent any real individual, company, product, or event, unless
      otherwise noted.</span></font></p>
     </td>
    </tr>
    <tr>
     <td vAlign="top" width="18"></td>
     <td vAlign="top"></td>
    </tr>
    <tr>
     <td colSpan="2" vAlign="top"><img alt border="0" hspace="0" src="http://domaindlx.com/asms/Img/ts.gif" vspace="10" width="1" height="1"></td>
    </tr>
   </tbody>
  </table>

