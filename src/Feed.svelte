<script>
    export let imageUrl;

    let liked = false;

    function like() {
        liked = !liked;
    }

    function downloadImage() {
        const link = document.createElement("a");
        link.href = imageUrl;
        link.download = "meme.jpg";
        link.click();
    }
</script>

<br />
<div class="feed">
    <img src={imageUrl} alt="" class="image" />
    <div class="actions">
        <button class="like" on:click={like}>
            {#if liked}
                <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="16"
                    height="16"
                    fill="currentColor"
                    class="bi bi-emoji-laughing-fill"
                    viewBox="0 0 16 16"
                >
                    <path
                        d="M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16zM7 6.5c0 .501-.164.396-.415.235C6.42 6.629 6.218 6.5 6 6.5c-.218 0-.42.13-.585.235C5.164 6.896 5 7 5 6.5 5 5.672 5.448 5 6 5s1 .672 1 1.5zm5.331 3a1 1 0 0 1 0 1A4.998 4.998 0 0 1 8 13a4.998 4.998 0 0 1-4.33-2.5A1 1 0 0 1 4.535 9h6.93a1 1 0 0 1 .866.5zm-1.746-2.765C10.42 6.629 10.218 6.5 10 6.5c-.218 0-.42.13-.585.235C9.164 6.896 9 7 9 6.5c0-.828.448-1.5 1-1.5s1 .672 1 1.5c0 .501-.164.396-.415.235z"
                    />
                </svg>
            {:else}
                <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="16"
                    height="16"
                    fill="currentColor"
                    class="bi bi-emoji-laughing"
                    viewBox="0 0 16 16"
                >
                    <path
                        d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"
                    />
                    <path
                        d="M12.331 9.5a1 1 0 0 1 0 1A4.998 4.998 0 0 1 8 13a4.998 4.998 0 0 1-4.33-2.5A1 1 0 0 1 4.535 9h6.93a1 1 0 0 1 .866.5zM7 6.5c0 .828-.448 0-1 0s-1 .828-1 0S5.448 5 6 5s1 .672 1 1.5zm4 0c0 .828-.448 0-1 0s-1 .828-1 0S9.448 5 10 5s1 .672 1 1.5z"
                    />
                </svg>
            {/if}
        </button>
        <button class="download" on:click={downloadImage}>
            <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-arrow-down-circle-fill"
                viewBox="0 0 16 16"
            >
                <path
                    d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zM8.5 4.5a.5.5 0 0 0-1 0v5.793L5.354 8.146a.5.5 0 1 0-.708.708l3 3a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 10.293V4.5z"
                />
            </svg></button
        >
    </div>
</div>
<br />

<style>
    .feed {
        background: rgba(241, 238, 238, 0.094);
        color: #fff;
        padding: 5px;
        width: 80%;
        height: auto;
        display: flex;
        flex-direction: column;
        gap: 5px;
        justify-content: center;
        align-items: left;
        position: relative; /* Added position: relative */
    }

    .feed img {
        width: 100%;
        height: 100%;
    }
    /* when on phones, make it wider */
    @media only screen and (max-width: 600px) {
        .feed {
            width: 90%;
        }
    }
    .actions {
        width: 100%;
        display: flex;
        flex-direction: row;
        gap: 5px;
        justify-content: space-evenly;
        align-items: center;
    }
    .actions button {
        width: 100%;
        height: 100%;
        border: none;
        padding: 5px;
        font-size: 1rem;
        font-weight: 600;
        cursor: pointer;
    }
</style>
