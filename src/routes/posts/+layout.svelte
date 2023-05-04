
<div class="drawer drawer-mobile">
    <input id="my-drawer-2" type="checkbox" class="drawer-toggle" />
    <div class="drawer-content flex flex-col items-center mt-32">
        <slot />
      <label for="my-drawer-2" class="btn btn-primary drawer-button lg:hidden">Open drawer</label>
    
    </div> 
    <div class="drawer-side">
      <label for="my-drawer-2" class="drawer-overlay"></label> 
      <ul class="menu p-4 w-80 bg-stone-400 text-base-content rounded-box mt-8 my-auto">
        <!-- Sidebar content here -->
        <li class="text-lg">Posts</li>
        <li><a href="/pages/one">One</a></li>
        <li><a href="/pages/two">Two</a></li>
      </ul>
    
    </div>
  </div>