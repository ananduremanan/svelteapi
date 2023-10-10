<script lang="ts">
  let userId: any;
  let userData: any;
  $: userName = userData && userData.userName;
  $: userGender = userData && userData.userGender;
  $: userAvatar = userData && userData.userAvatar;

  const handleUserId = (event: any) => {
    event.preventDefault();
    userId = event.target.value;
  };

  const fetchUserData = async () => {
    try {
      const res = await fetch(
        `http://localhost:3000/getUserDetails?id=${userId}`
      );
      const data = await res.json();
      userData = data;
      console.log(userData);
    } catch (error) {
      console.log(error);
    }
  };
</script>

<main class="flex flex-col justify-center items-center h-screen">
  <div class="flex gap-1">
    <input
      type="text"
      placeholder="Enter User ID"
      class="bg-slate-200 p-2 rounded-lg"
      on:input={handleUserId}
    />
    <button
      type="submit"
      class="bg-orange-300 p-2 rounded-lg"
      on:click={fetchUserData}>Search</button
    >
  </div>
  <div class="mt-2 flex flex-col">
    {#if !userName}
      <p>Search with User ID</p>
    {:else}
      <div class="flex gap-2 bg-yellow-300 p-2 rounded-lg w-64">
        <img src={userAvatar} width="50" height="50" alt="user avatar" />
        <div>
          <h1>Name: {userName}</h1>
          <h1>Gender: {userGender}</h1>
        </div>
      </div>
    {/if}
  </div>
</main>
