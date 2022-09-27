<template>
  <div class="login">
    <div class="card">
      <div class="card__left">
        <img src="@/assets/logotip.png" alt="logotip" />
      </div>
      <div class="card__right">
        <!--<img class="user_photo" src="@/assets/man.png" alt="logotip">-->
        <div class="flex flex-col justify-center">
          <span class="title">Вход в систему</span>
          <!--<input type="text" class="mt-10" placeholder="Логин" />-->
          <div class="mt-10">
            <label class="text-[#141839cc] text-sm">Логин</label>
            <div class="relative">
              <img
                width="20px"
                class="absolute left-5 top-1/2 -translate-y-1/2"
                src="../../assets/icons/user.svg"
                alt="user"
              />
              <input
                type="text"
                name="text"
                autocomplete="off"
                required
                placeholder="Логин"
                class="mt-1 w-full py-[14px] px-[24px] pl-11 focus:outline-none mainColor border borderBox rounded-[12px]"
              />
            </div>
          </div>
          <div class="mt-8">
            <label class="text-[#141839cc] text-sm">Пароль</label>
            <div class="relative">
              <img
                width="20px"
                class="absolute left-5 top-1/2 -translate-y-1/2"
                src="../../assets/icons/lock.svg"
                alt="user"
              />
              <input
                type="text"
                name="text"
                autocomplete="off"
                required
                placeholder="Пароль"
                class="mt-1 w-full py-[14px] px-[24px] pl-11 focus:outline-none mainColor border borderBox rounded-[12px]"
              />
            </div>
          </div>
          <!--<input type="text" class="form-control mt-10" placeholder="Пароль" />-->
          <button
            class="basicBtn w-[400px] bg-[#2597DE] flex justify-center text-white mt-14 text-center hover:bg-opacity-80 duration-200"
          >
            Войти
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
