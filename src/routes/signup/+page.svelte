<style>
    .form-container {
        width: 300px;
        padding: 16px;
        background-color: white;
        border: 1px solid black;
        margin: 0 auto;
    }
</style>

<script>
    let user = {
        email: '',
        pw: '',
        nickname: '',
        bank_account: '',
        bank: '',
        address: '',
        height: '',
        weight: '',
        gender: '',
        age: ''
    };

    async function submitForm(event) {
    event.preventDefault();
    try {
        const response = await fetch('http://localhost:8080/signup', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(user)
        });
        if (response.ok) {
            alert("폼이 성공적으로 전송되었습니다.");
        } else {
            const error = await response.json();
            alert("오류가 발생했습니다: " + error.error);
        }
    } catch (error) {
        console.error("서버 요청 중 에러가 발생했습니다:", error);
    }
}

</script>

<div class="form-container">
    <form action="http://localhost:8080/signup" method="POST" enctype="application/x-www-form-urlencoded" on:submit={submitForm}>
        <label for="email">Email:</label><br>
        <input type="text" id="email" name="email" bind:value={user.email}><br>
        <label for="pw">Password:</label><br>
        <input type="password" id="pw" name="pw" bind:value={user.pw}><br>
        <label for="nickname">Nickname:</label><br>
        <input type="text" id="nickname" name="nickname" bind:value={user.nickname}><br>
        <label for="bank_account">Bank Account:</label><br>
        <input type="text" id="bank_account" name="bank_account" bind:value={user.bank_account}><br>
        <label for="bank">Bank:</label><br>
        <input type="text" id="bank" name="bank" bind:value={user.bank}><br>
        <label for="address">Address:</label><br>
        <input type="text" id="address" name="address" bind:value={user.address}><br>
        <label for="height">Height:</label><br>
        <input type="text" id="height" name="height" bind:value={user.height}><br>
        <label for="weight">Weight:</label><br>
        <input type="text" id="weight" name="weight" bind:value={user.weight}><br>
        <label for="gender">Gender:</label><br>
        <input type="radio" id="male" name="gender" value="true" bind:group={user.gender}>
        <label for="male">남자</label><br>
        <input type="radio" id="female" name="gender" value="false" bind:group={user.gender}>
        <label for="female">여자</label><br>
        <label for="age">Age:</label><br>
        <input type="text" id="age" name="age" bind:value={user.age}><br>
        <input type="submit" value="Submit">
    </form>
</div>
