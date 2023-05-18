<div class="sidebar">
    <div class="userIcons">
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
        <div class="userIcon">
            <img src="https://picsum.photos/50" alt="" />
        </div>
    </div>
</div>

<style>
    .sidebar {
        height: 100vh;
        width: 80px;
        background: #333;
        color: #fff;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }
    /* if small screen change the height and width */

    .userIcons {
        display: flex;
        background-color: red;
        gap: 40px;
        align-items: center;
        height: 100%;
        padding: 10px;
        flex-direction: column;
        justify-content: space-between;
        overflow-x: hidden;
        overflow-y: scroll;
    }
    .userIcon {
        height: 60px;
        width: 60px;
        border-radius: 50%;
    }

    .userIcon img {
        height: 100%;
        width: 100%;
        object-fit: cover;
    }

    @media screen and (max-width: 800px) {
        .sidebar {
            height: 80px;
            width: 100%;
        }
        .userIcons {
            margin: 0 10px 0 10px;
            width: 90%;
            flex-direction: row;
            justify-content: space-between;
            gap: 25px;
            overflow-x: scroll;
            overflow-y: hidden;
        }
    }
    /* hide scroll bars */
    .userIcons::-webkit-scrollbar {
        display: none;
    }
</style>
