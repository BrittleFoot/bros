<script>
  import "../app.css";
  import NavItem from "../lib/NavItem.svelte";
	import NavDropDown from '../lib/NavDropDown.svelte';
</script>

<div class='fixed w-full top-0 lg:px-8 px-5 lg:pt-8 pt-5 z-70'>
  <nav class='flex h-full border-b border-white items-center justify-center max-w-11xl mx-auto border-opacity-0'>
    <div class='flex-grow'>
      <NavItem url='/' name='Home'/>
    </div>
    <div class='flex space-x-2'>
      <NavItem url='/brotherhood' name='The Brotherhood'/>
      <NavItem url='/roadmap' name='Roadmap'/>
      <NavDropDown name='More' urls={['/careers', '/manifesto']}/>
    </div>
  </nav>
</div>

<slot />