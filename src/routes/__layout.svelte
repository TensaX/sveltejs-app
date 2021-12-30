<script>
  import "../app.css";
  
  import A from '../components/A.svelte'
</script>

<nav>
  <ul>
    <li>
      <A href="/">Home</A>
    </li>
    <li>
      <A href="/signin">SignIn</A>
    </li>
    <li>
      <A href="/signup">SignUp</A>
    </li>
  </ul>
</nav>

<slot />

<style>
  ul{
    display: flex;
    margin:0;
    padding:0;
  }
  li{
    
    margin-bottom: 15x;
    margin-top: 20px;
    margin-left: 20px;
    font-weight: bold;
  }
</style>