<script lang="ts">
    import * as Table from "$lib/components/ui/table/index.js";
    import { ScrollArea } from "$lib/components/ui/scroll-area/index.js";
    import {onDestroy, onMount} from "svelte";
    let listElement: HTMLElement | null = null;

    let count = 0;
    let invoices = [
        {
            invoice: "User " + count++,
            paymentStatus: "1m",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "5m",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "7m",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "23m",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "45m",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "1hr",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "2.4hr",
            totalAmount: "SL1",
            paymentMethod: "Online"
        },
        {
            invoice: "User " + count++,
            paymentStatus: "5d",
            totalAmount: "SL1",
            paymentMethod: "Online"
        }
    ];

    function load() {
        for(let i = 0; i < 10; i++) {
            invoices.push({
                invoice: "User " + count++,
                paymentStatus: "30m ago",
                totalAmount: "SL1",
                paymentMethod: "Offline"
            });
        }
        invoices = invoices;
    }

    let scrollHandler = function () {
        if (
            listElement &&
            listElement.scrollTop + listElement.clientHeight + 1 >=
            listElement.scrollHeight
        ) {
            load();
        }
    };

    onMount(() => {
        if (listElement) {
            listElement.addEventListener("scroll", scrollHandler);
        }
    });

    onDestroy(() => {
        if (listElement) {
            listElement.removeEventListener("scroll", scrollHandler);
        }
    });
</script>

<ul class="scroll-area" bind:this={listElement}>
    <Table.Root>
        <Table.Header>
            <Table.Row>
                <Table.Head>User</Table.Head>
                <Table.Head>Session Time</Table.Head>
                <Table.Head>Status</Table.Head>
                <Table.Head>Server</Table.Head>
            </Table.Row>
        </Table.Header>
        <Table.Body>
            {#each invoices as invoice, i (i)}
                <Table.Row>
                    <Table.Cell class="font-medium">{invoice.invoice}</Table.Cell>
                    <Table.Cell>{invoice.paymentStatus}</Table.Cell>
                    <Table.Cell>{invoice.paymentMethod}</Table.Cell>
                    <Table.Cell>{invoice.totalAmount}</Table.Cell>
                    <Table.Cell class="font-bold">&hellip;</Table.Cell>
                </Table.Row>
            {/each}
        </Table.Body>
    </Table.Root>
</ul>

<style>
    .scroll-area {
        width: 650px;
        height: 400px;
        overflow-y: auto;
        position: relative;
        padding-left: 10px;
        padding-right: 3px;
        background-color: #1c1c1c;
    }

    .scroll-content {
    }

    .scroll-area::-webkit-scrollbar {
        width: 8px;
        transition: opacity 0.3s;
    }

    .scroll-area::-webkit-scrollbar-thumb {
        background-color: gray;
        border-radius: 4px;
        min-height: 70px;
    }

    .scroll-area:hover::-webkit-scrollbar-thumb {
        background-color: #3d3d3d;

    }

    .scroll-area::-webkit-scrollbar-track {
        background: transparent;
    }

    .scroll-area:not(:hover)::-webkit-scrollbar-thumb {
        transition-delay: 2s;
        background-color: transparent;
        opacity: 0;
    }
    ul {
        width: 800px;
        height: 400px;
        overflow-y: auto;
        position: relative;
        border: 1px solid #ccc;
        padding-left: 10px;
        padding-right: 3px;
        background-color: #09090B;
    }

    /* Optional eye candy below: */
    li {
        padding: 10px;
        list-style-type: none;
    }
    li:hover {
        background: #ccc;
    }
</style>